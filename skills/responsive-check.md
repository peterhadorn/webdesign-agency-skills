---
name: responsive-check
description: "Test across breakpoints, screenshot each, report layout breaks, and fix with /adapt"
---

# /responsive-check — Cross-Breakpoint Testing & Fixes

Test a page across every major breakpoint. Screenshot each, report layout breaks, fix with `/adapt`.

```
/responsive-check [url-or-file]
```

---

## Step 0: Browser Check

This skill requires browser tools for viewport resizing and screenshots:

1. **Check for Chrome DevTools MCP** — look for tools like `mcp__chrome-devtools__resize_page`, `mcp__chrome-devtools__take_screenshot`
2. **Check for Playwright MCP** — look for tools like `mcp__playwright__browser_resize`, `mcp__playwright__browser_take_screenshot`

**If neither is available**, stop and guide the user:

```
This skill needs a browser for viewport testing and screenshots:

1. **Chrome DevTools MCP** (recommended — viewport control + screenshots):
   claude plugin add superpowers-chrome

2. **Playwright MCP** (alternative):
   claude mcp add playwright -- npx @playwright/mcp@latest

Install one or both, then re-run /responsive-check.
```

**If available**, proceed.

---

## Step 1: Define Breakpoints

Test at these standard breakpoints (width × height):

| Name | Width | Height | Represents |
|------|-------|--------|-----------|
| Mobile S | 320px | 568px | iPhone SE, small Android |
| Mobile M | 375px | 812px | iPhone 12/13/14, standard Android |
| Mobile L | 428px | 926px | iPhone 14 Pro Max, large Android |
| Tablet Portrait | 768px | 1024px | iPad, Android tablet (portrait) |
| Tablet Landscape | 1024px | 768px | iPad landscape |
| Desktop | 1280px | 800px | Standard laptop |
| Desktop L | 1440px | 900px | Large laptop / external display |
| Ultrawide | 1920px | 1080px | Full HD monitor |

If the site has custom breakpoints (check its CSS for `@media` queries), add those too.

---

## Step 2: Screenshot Each Breakpoint

For each breakpoint:

1. Resize viewport: `mcp__chrome-devtools__resize_page` or `mcp__playwright__browser_resize`
2. Wait for layout to settle (300ms minimum)
3. Take a full-page screenshot: `mcp__chrome-devtools__take_screenshot` or `mcp__playwright__browser_take_screenshot`
4. Save as `responsive/[domain]-[breakpoint-name].png`

Also take a DOM snapshot at each breakpoint to inspect element visibility and overflow:
- `mcp__chrome-devtools__take_snapshot` or `mcp__playwright__browser_snapshot`

---

## Step 3: Analyze Each Breakpoint

Review each screenshot and snapshot. Check for these issues:

### Layout Breaks

| Issue | How to Detect | Severity |
|-------|--------------|----------|
| Horizontal overflow / scrollbar | Content wider than viewport, horizontal scroll appears | Critical |
| Overlapping elements | Text on top of images, buttons overlapping nav | Critical |
| Content cut off | Text or images clipped by container | Critical |
| Invisible content | Elements with `display:none` that shouldn't be hidden | High |
| Navigation unusable | Menu items unreachable, hamburger missing, dropdown off-screen | High |
| Touch targets too small | Buttons/links < 44px on mobile breakpoints | High |
| Text unreadable | Font too small (< 14px on mobile), line too long (> 80ch on desktop) | High |
| Images distorted | Stretched, squished, or wrong aspect ratio | Medium |
| Excessive whitespace | Large empty gaps that break visual flow | Medium |
| Footer gap | White space below footer (body shorter than viewport) | Medium |
| Content reflow | Content order changes in a confusing way | Medium |
| Inconsistent spacing | Padding/margins visibly different across breakpoints | Low |

### Check for Missing Responsive Patterns

| Pattern | Expected Behavior | Missing If |
|---------|------------------|------------|
| Navigation | Hamburger/drawer on mobile, full nav on desktop | Full nav visible on mobile or hamburger on desktop |
| Images | Responsive sizing, art direction for key images | Fixed-width images, same crop at all sizes |
| Typography | Scales down on mobile (clamp or breakpoint-based) | Same font sizes at 320px and 1920px |
| Grid/columns | Stack on mobile, multi-column on desktop | Multi-column at 320px or single-column at 1920px |
| Tables | Scroll, stack, or reflow on mobile | Table overflows viewport on mobile |
| Forms | Full-width inputs on mobile | Fixed-width inputs that overflow or look tiny |

---

## Step 4: Report

Present findings grouped by severity:

```markdown
## Responsive Check — [domain]

Tested across 8 breakpoints (320px–1920px).

### Critical Issues
- **Horizontal overflow at 320px** — Hero section has fixed 400px width, causes horizontal scroll
- **Navigation hidden at 768px** — No hamburger menu, nav links overflow off-screen

### High Priority
- **Touch targets at 375px** — Footer links are 12px tall, need minimum 44px
- **Text unreadable at 320px** — Body text is 11px, increase to 16px minimum

### Medium Priority
- **Image distortion at 428px** — Team photo stretched, needs object-fit: cover
- **Footer gap at 1920px** — Page content doesn't fill viewport height

### Low Priority
- **Inconsistent card spacing** — 16px gap on mobile, 24px on tablet, 32px on desktop (not intentional)

### Screenshots
- [Mobile S (320px)](responsive/example-com-mobile-s.png)
- [Mobile M (375px)](responsive/example-com-mobile-m.png)
- [Tablet (768px)](responsive/example-com-tablet-portrait.png)
- [Desktop (1280px)](responsive/example-com-desktop.png)
- [Ultrawide (1920px)](responsive/example-com-ultrawide.png)
```

Wait for user confirmation before fixing.

---

## Step 5: Fix

For each issue, apply the appropriate fix:

### CSS Fixes by Issue Type

| Issue | Fix Approach |
|-------|-------------|
| Horizontal overflow | `max-width: 100%`, `overflow-x: hidden` on container, fix fixed-width elements |
| Overlapping elements | Check `position: absolute/fixed`, adjust `z-index`, use flexbox/grid |
| Text too small on mobile | Use `clamp()` for fluid typography: `font-size: clamp(1rem, 2.5vw, 1.25rem)` |
| Line too long on desktop | Set `max-width: 65ch` on text containers |
| Touch targets too small | `min-height: 44px; min-width: 44px; padding: 12px` |
| Image distortion | `object-fit: cover` or `contain`, set `aspect-ratio` |
| Missing hamburger | Add responsive nav with `@media (max-width: 768px)` |
| Fixed-width elements | Replace `width: Xpx` with `max-width: 100%` or percentage |
| Footer gap | `min-height: 100vh` on body/main, or flexbox sticky footer |
| Table overflow | `overflow-x: auto` wrapper, or stack cells vertically on mobile |

### After Fixing

Run `/adapt` on the target to catch anything manual fixes missed. `/adapt` handles responsive behavior systematically.

Then run `/polish` as a final pass.

---

## Step 6: Re-verify

After all fixes:

1. Re-screenshot all breakpoints that had issues
2. Compare before/after
3. Report:

```
## Responsive Check — Fixed

| Breakpoint | Issues Found | Issues Fixed | Remaining |
|-----------|-------------|-------------|-----------|
| Mobile S (320px) | 3 | 3 | 0 |
| Mobile M (375px) | 2 | 2 | 0 |
| Tablet (768px) | 2 | 2 | 0 |
| Desktop (1280px) | 0 | — | — |
| Ultrawide (1920px) | 1 | 1 | 0 |

All breakpoints clean. ✓
```

If issues remain, loop back to Step 5.

---

## Rules

1. Always screenshot before fixing — visual evidence, not assumptions
2. Mobile first — fix 320px issues before desktop issues
3. Test the extremes — 320px and 1920px catch the most breaks
4. Don't hide problems — `overflow: hidden` is a bandaid, not a fix
5. Check both portrait and landscape on tablet — they break differently
6. Never remove content on mobile — restructure it, don't hide it (unless truly irrelevant)
