---
name: performance-audit
description: "Core Web Vitals deep dive — LCP, CLS, INP analysis with specific fixes. Goes beyond Lighthouse scores into real-world performance."
---

# /performance-audit — Core Web Vitals Deep Dive

Measure, diagnose, and fix real-world performance. Goes deeper than a Lighthouse score — analyzes LCP, CLS, INP with element-level attribution and specific fixes.

```
/performance-audit [url-or-file]
```

---

## Step 0: Browser Check

This skill requires browser tools for performance measurement:

1. **Check for Chrome DevTools MCP** — look for tools like `mcp__chrome-devtools__lighthouse_audit`, `mcp__chrome-devtools__performance_start_trace`
2. **Check for Playwright MCP** — look for tools like `mcp__playwright__browser_navigate`

**If neither is available**, stop and guide the user:

```
This skill needs a browser for performance measurement:

1. **Chrome DevTools MCP** (recommended — full performance tracing):
   claude plugin add superpowers-chrome

2. **Playwright MCP** (alternative — basic metrics):
   claude mcp add playwright -- npx @playwright/mcp@latest

Chrome DevTools is strongly preferred — it provides Performance traces
and Lighthouse audits. Install it, then re-run /performance-audit.
```

**If available**, proceed. Prefer Chrome DevTools for this skill.

---

## Step 1: Baseline Measurement

### 1a: Lighthouse Performance Audit

Run Lighthouse on both mobile and desktop:

1. Navigate to the page
2. Run `mcp__chrome-devtools__lighthouse_audit` (device: mobile, mode: navigation)
3. Run `mcp__chrome-devtools__lighthouse_audit` (device: desktop, mode: navigation)
4. Extract the Performance score and all metric values

### 1b: Performance Trace

Capture a real performance trace:

1. `mcp__chrome-devtools__performance_start_trace`
2. Navigate to the page (cold load)
3. `mcp__chrome-devtools__performance_stop_trace`
4. `mcp__chrome-devtools__performance_analyze_insight` — extract timing breakdowns

### 1c: Network Analysis

1. `mcp__chrome-devtools__list_network_requests` — capture all requests during page load
2. Identify:
   - Total transfer size
   - Number of requests
   - Render-blocking resources (CSS/JS in `<head>` without `async`/`defer`)
   - Largest assets by size
   - Third-party requests and their impact
   - Uncompressed resources (missing gzip/brotli)

### 1d: Record Baseline

```
## Baseline — [date]

| Metric | Mobile | Desktop | Target |
|--------|--------|---------|--------|
| Performance Score | XX | XX | 90+ |
| LCP | X.Xs | X.Xs | ≤2.5s |
| CLS | X.XX | X.XX | ≤0.1 |
| INP | XXms | XXms | ≤200ms |
| FCP | X.Xs | X.Xs | ≤1.8s |
| TTFB | XXms | XXms | ≤800ms |
| Speed Index | X.Xs | X.Xs | ≤3.4s |
| Total Blocking Time | XXms | XXms | ≤200ms |

Transfer: XXX KB over NN requests
Render-blocking: N resources (XX KB)
```

---

## Step 2: Diagnose by Metric

Work through each Core Web Vital that's failing. The diagnosis determines the fix.

### LCP (Largest Contentful Paint) — Target: ≤2.5s

**Identify the LCP element** from the Lighthouse report (`largest-contentful-paint-element` audit).

| LCP Element | Common Cause | Fix |
|-------------|-------------|-----|
| `<img>` (hero image) | Unoptimized, no preload, wrong format | Convert to WebP/AVIF, add `<link rel="preload">`, set `fetchpriority="high"`, explicit `width`/`height` |
| `<img>` (below fold loaded first) | Missing lazy loading on other images stealing bandwidth | Add `loading="lazy"` to all images except LCP, `loading="eager"` on LCP image |
| Background image (CSS) | Discovered late (after CSS parse) | Move to `<img>` tag or add `<link rel="preload" as="image">` |
| Text block | Render-blocking CSS/JS, web font delay | Inline critical CSS, `font-display: swap`, preload key fonts |
| Video poster | Large poster image, no preload | Optimize poster, preload it |

**Server-side LCP causes:**
| Symptom | Fix |
|---------|-----|
| TTFB > 800ms | Server optimization, CDN, caching headers |
| Redirect chains | Eliminate intermediate redirects |
| No compression | Enable gzip/brotli on server |

### CLS (Cumulative Layout Shift) — Target: ≤0.1

**Identify shifting elements** from the Lighthouse report (`layout-shift-elements` audit).

| Shift Source | Fix |
|-------------|-----|
| Images without dimensions | Add explicit `width` and `height` attributes |
| Ads/embeds without reserved space | Use `aspect-ratio` or `min-height` on container |
| Web fonts causing reflow | `font-display: swap` + `size-adjust` descriptor, or preload fonts |
| Dynamic content injected above fold | Reserve space with CSS, or inject below viewport |
| Late-loading CSS changing layout | Inline critical CSS, async non-critical |
| Animations using `top`/`left`/`width`/`height` | Use `transform` and `opacity` only |

### INP (Interaction to Next Paint) — Target: ≤200ms

INP measures responsiveness. If failing:

| Symptom | Diagnosis | Fix |
|---------|-----------|-----|
| All interactions slow | Long main-thread tasks | Break up JS bundles, defer non-critical, use `requestIdleCallback` |
| Specific button/form slow | Heavy event handler | Optimize handler, debounce, move work to Web Worker |
| Scroll jank | Forced synchronous layout | Avoid `.offsetHeight` reads in scroll handlers, use `will-change` |
| Typing lag in inputs | Expensive `input` event handlers | Debounce, use `requestAnimationFrame` |

### FCP / TTFB (Supporting Metrics)

| Metric | If Failing | Fix |
|--------|-----------|-----|
| FCP > 1.8s | Render-blocking resources | Inline critical CSS (< 14KB), defer JS with `async`/`defer`, preload key resources |
| TTFB > 800ms | Slow server response | CDN, server-side caching, reduce redirects, optimize database queries |

---

## Step 3: Fix

Apply fixes in this order (each fix builds on the previous):

| Phase | Fixes | Why first |
|-------|-------|-----------|
| 1. Delivery | Compression, CDN, caching headers, redirect elimination | Reduces raw transfer time |
| 2. Critical path | Inline critical CSS, defer JS, preload LCP asset + fonts | Unblocks rendering |
| 3. Assets | Image optimization (WebP/AVIF, sizing, lazy loading) | Reduces largest payloads |
| 4. Layout stability | Explicit dimensions, reserved space, font `size-adjust` | Eliminates shifts |
| 5. Interactivity | Code splitting, debouncing, Web Workers | Frees main thread |

After each fix, note what was changed:
```
Fixed: Added width/height to 12 images, preloaded hero image, deferred 3 JS files
```

---

## Step 4: Re-measure

After fixes:

1. Run Lighthouse again (mobile + desktop)
2. Run another performance trace if changes were significant
3. Compare to baseline:

```
## Results

| Metric | Before | After | Target | Status |
|--------|--------|-------|--------|--------|
| Performance | 54 | 92 | 90+ | ✓ |
| LCP | 4.2s | 1.8s | ≤2.5s | ✓ |
| CLS | 0.34 | 0.02 | ≤0.1 | ✓ |
| INP | 380ms | 150ms | ≤200ms | ✓ |
```

If any metric still fails, loop back to Step 2 for that specific metric.

---

## Step 5: Summary

```
## Performance Audit — [domain]

Improved Performance score from XX to XX.

### Fixed
- [list each fix with before/after metric impact]

### Core Web Vitals
| Metric | Before | After | Status |
|--------|--------|-------|--------|
| LCP | X.Xs | X.Xs | ✓/✗ |
| CLS | X.XX | X.XX | ✓/✗ |
| INP | XXms | XXms | ✓/✗ |

### Recommendations Not Applied
- [anything skipped and why — e.g., "CDN setup requires DNS changes"]
```

---

## Rules

1. Always measure before fixing — never guess at performance problems
2. Fix the biggest bottleneck first — one large improvement beats five small ones
3. Re-measure after each round — one fix can regress another metric
4. Mobile first — mobile scores are always worse and matter more
5. Real metrics over scores — a Performance score of 85 with all green Core Web Vitals is better than 95 with a failing LCP
