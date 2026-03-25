---
name: improve
description: "Targeted design improvement loop — audit, recommend, fix, verify"
---

# /improve — Targeted Design Improvement

Diagnose → recommend → fix → verify. Only runs what's needed.

```
/improve [url-or-file]
```

---

## Step 0: Browser Check (URL targets only)

If the target is a URL (not a local file), check if browser MCP tools are available:

1. **Check for Playwright MCP** — look for tools like `mcp__playwright__browser_navigate`
2. **Check for Chrome DevTools MCP** — look for tools like `mcp__chrome-devtools__navigate_page`

**If neither is available and the target is a URL**, stop and guide the user:

```
To improve a live URL, you need a browser MCP server:

1. **Playwright MCP** (headless, best for automated audits):
   claude mcp add playwright -- npx @playwright/mcp@latest

2. **Chrome DevTools MCP** (controls your real browser):
   claude plugin add superpowers-chrome

Install one or both, then re-run /improve.

Alternatively, pass a local file path instead — no browser needed.
```

**If the target is a local file**, skip this step entirely.

---

## Step 1: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first.

## Step 2: Diagnose

Run on the target:

1. `/audit` — accessibility, performance, theming, responsive, anti-patterns
2. `/critique` — visual hierarchy, typography, color, spacing, emotional impact

Save both reports. Do not fix anything yet.

## Step 3: Recommend

### Synthesize findings

1. **Read** both audit and critique reports
2. **Map** each finding to an Impeccable command using the table below
3. **Deduplicate** — if audit and critique both flag the same issue, merge into one finding
4. **Group** by command — if three issues all need `/typeset`, they become one item
5. **Order** by severity: critical issues first, polish last
6. **Check for conflicts** (see Conflict Table below)
7. **Present** to user:

```
## Recommended Fixes

1. /typeset — 3 issues: weak heading scale, inconsistent weights, tight line-height
2. /colorize — 2 issues: low CTA contrast, monochrome sections
3. /arrange — 1 issue: uneven section spacing

⚠️ Note: /bolder + /clarify selected — bolder may increase visual weight that clarify tries to reduce. Will run /clarify last to preserve readability.

Run all? Or select which to apply:
```

Wait for user selection.

### Finding-to-Command Mapping

| Finding Category | Command | What It Does |
|-----------------|---------|--------------|
| Typography issues (scale, hierarchy, line-height, font pairing) | `/typeset` | Fix type scale and font relationships |
| Color/contrast issues (palette, contrast ratios, color harmony) | `/colorize` | Rebuild or adjust color system |
| Layout/spacing issues (alignment, grid, whitespace, padding) | `/arrange` | Fix spatial relationships and layout structure |
| Too bland, safe, or generic | `/bolder` | Push the design toward more confident choices |
| Too noisy, aggressive, or cluttered | `/quieter` | Reduce visual noise and create breathing room |
| Motion/animation gaps (no transitions, static interactions) | `/animate` | Add purposeful motion and micro-interactions |
| Copy/label clarity (confusing labels, vague CTAs, jargon) | `/clarify` | Rewrite UI text for clarity and action |
| Over-engineered (too many elements, unnecessary complexity) | `/distill` | Strip to essentials, remove what doesn't earn its place |
| Error handling/edge cases (empty states, loading, failures) | `/harden` | Add resilience for real-world conditions |
| Performance issues (heavy assets, render blocking, layout shifts) | `/optimize` | Fix performance bottlenecks |
| Responsive breakpoints (broken on mobile/tablet, missing queries) | `/adapt` | Fix responsive behavior across viewports |
| Missing delight/personality (functional but forgettable) | `/delight` | Add moments of personality without sacrificing clarity |
| Design system inconsistency (mixed patterns, one-off styles) | `/normalize` | Align to a consistent component/token system |
| Onboarding/empty states (no guidance, blank screens, cold starts) | `/onboard` | Design first-run and empty-state experiences |
| Technically ambitious effects (3D, shaders, advanced CSS, scroll-driven) | `/overdrive` | Push technical boundaries for standout moments |

### Ambiguous Findings

| Finding | Seems like | Actually | Why |
|---------|-----------|----------|-----|
| "Buttons look different on every page" | `/colorize` | `/normalize` | Consistency problem, not color problem |
| "Too much whitespace" | `/arrange` | `/distill` if sparse, `/arrange` if spacing wrong | Check content density vs spacing values |
| "Text is hard to read" | `/typeset` | `/colorize` if contrast, `/typeset` if scale/weight | Check what specifically makes it hard |
| "Page feels slow" | `/optimize` | `/animate` if perceived, `/optimize` if measured | Check actual vs perceived performance |

## Step 4: Fix

Run each selected command in the correct order:

| Phase | Commands | Why first |
|-------|----------|-----------|
| 1. Structure | `/distill`, `/arrange`, `/adapt` | Layout defines the canvas — fixing color on a broken grid wastes effort |
| 2. Systems | `/normalize`, `/harden`, `/onboard` | Consistent tokens and resilience before visual refinement |
| 3. Visual | `/typeset`, `/colorize`, `/clarify` | Type and color work within the established structure |
| 4. Personality | `/bolder` or `/quieter`, `/delight`, `/animate` | Personality layer on top of a solid foundation |
| 5. Ambitious | `/overdrive` | Technical effects last — they depend on everything below being stable |

After each command, one-line summary:
```
/typeset — Fixed heading scale (h1-h4), increased body line-height to 1.6
```

## Step 5: Polish

Run `/polish` as the final pass. Always.

## Step 6: Verify

Show a delta summary, then ask whether to continue:

```
## Progress

Round 1 found 8 issues. After fixes: 3 remain.
✓ Fixed: heading scale, CTA contrast, card grid spacing
→ Remaining: mobile nav overlap, image compression, empty search state

Run another audit to verify? Or done?
```

- **yes** → loop back to Step 2. The new audit will catch regressions and remaining issues.
- **done** → output final summary of all changes across all rounds.

Two loops is normal. Rarely need more than three.

---

## Conflict Table

Some commands can interfere with each other. When both are selected, apply the mitigation:

| Combination | Risk | Mitigation |
|-------------|------|------------|
| `/bolder` + `/clarify` | Bolder increases visual weight; clarify reduces it | Run `/clarify` after `/bolder` — readability wins |
| `/bolder` + `/quieter` | Contradictory intent | Ask user which direction they want — never run both |
| `/colorize` + `/normalize` | New colors may diverge from design system tokens | Run `/normalize` after `/colorize` to re-align |
| `/animate` + `/optimize` | Animations can hurt performance | Run `/optimize` after `/animate` to catch regressions |
| `/delight` + `/distill` | Delight adds; distill removes | Run `/distill` first, then `/delight` only on what survived |
| `/overdrive` + `/adapt` | Ambitious effects often break on mobile | Run `/adapt` after `/overdrive` to verify responsive behavior |

If a conflict isn't in this table, the execution order (Step 4) handles it.

---

## Rules

1. Never fix without diagnosing first
2. Never skip user approval on the recommendation list
3. Respect `.impeccable.md` — fixes must align with stated design context
4. One command, one concern — `/typeset` doesn't fix colors
5. Structure before visual before personality — always
6. Show progress between rounds — never re-audit silently
