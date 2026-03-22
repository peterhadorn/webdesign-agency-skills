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

## Step 1: Load

- **URL** — Navigate via Playwright to render the page
- **Local file** — Read the file into context
- If load fails: report error and abort

## Step 2: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first.

## Step 3: Diagnose

1. `/audit` — accessibility, performance, theming, responsive, anti-patterns
2. `/critique` — visual hierarchy, typography, color, spacing, emotional impact

Save both reports. Do not fix anything yet.

## Step 4: Recommend

See [_recommendation-loop.md](./_recommendation-loop.md) for the shared engine.

1. Map each finding to an Impeccable command
2. Group by command, order by severity
3. Present to user:

```
## Recommended Fixes

1. /typeset — 3 issues: weak heading scale, inconsistent weights, tight line-height
2. /colorize — 2 issues: low CTA contrast, monochrome sections
3. /arrange — 1 issue: uneven section spacing

Run all? Or select which to apply:
```

Wait for user selection.

## Step 5: Fix

Run each selected command in sequence:

1. Execute the command
2. One-line summary after each:
   ```
   /typeset — Fixed heading scale (h1-h4), increased body line-height to 1.6
   ```

**Order matters**: structural (`/arrange`, `/adapt`) before visual (`/colorize`, `/typeset`) before polish (`/delight`, `/animate`). Reorder if needed — explain why.

## Step 6: Polish

Run `/polish` as the final pass. Always.

## Step 7: Verify

Ask: "Run another audit to verify? Or done?"

- **yes** → loop back to Step 3
- **done** → complete

---

## Optional Extensions

- **Before/after screenshots** — Desktop + mobile comparison via Playwright
- **Performance comparison** — Load timing before vs after
- **Commit changes** — Stage and commit modified files

---

## Rules

1. Never fix without diagnosing first
2. Never skip user approval on the recommendation list
3. Respect `.impeccable.md` — fixes must align with stated design context
4. One command, one concern — `/typeset` doesn't fix colors
5. Structural before visual before polish
