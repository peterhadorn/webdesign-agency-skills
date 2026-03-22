---
name: improve
description: "Targeted design improvement loop — audit, recommend, fix, verify"
---

# /improve — Targeted Design Improvement

Systematic improvement workflow: diagnose issues, map them to the right Impeccable commands, apply fixes in priority order, and verify results.

## Input

```
/improve [url-or-file]
```

- **URL**: Live page loaded via Playwright
- **File path**: Local HTML/CSS/JS file(s)
- If no argument: ask the user what to improve

## Phase 0: Load

### Context Swap

1. Check for `.impeccable.md` in the project root
2. If missing: run `/teach-impeccable` first — the design context is required for accurate diagnosis
3. Read `.impeccable.md` and hold its design principles, brand personality, and aesthetic direction in context for all phases

### Load Target

- **URL provided**: Launch Playwright, navigate to the URL, take a full-page screenshot
- **File provided**: Read the file(s) into context
- **If load fails**: Report the error and abort. Do not guess at content.

## Phase 1: Diagnose

### Step 1.1 — Run Audits

Run both diagnostic commands against the loaded target:

1. **`/audit`** — Structural analysis: accessibility, semantic HTML, responsive behavior, performance signals, code quality
2. **`/critique`** — Design analysis: visual hierarchy, typography, color usage, spacing, consistency, emotional impact

Save both reports for reference. Do not fix anything yet.

### Step 1.2 — The Recommendation Loop

This is the core of the skill. Map every finding to the right fix.

1. Read both the audit and critique reports
2. Map each finding to an Impeccable command using this table:

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

3. Group findings by command — if three issues all need `/typeset`, they become one item
4. Order by severity: critical issues first, polish last
5. Present the recommendation list to the user:

```
## Recommended Fixes (from audit + critique)

1. /typeset — 3 issues: heading scale inconsistent, body line-height too tight, font weights not differentiated
2. /colorize — 2 issues: CTA contrast below 4.5:1, secondary palette muddy against background
3. /arrange — 1 issue: card grid breaks at tablet widths, uneven gutter spacing

Run all? Or select which to apply (e.g., "1 and 3", "skip 2"):
```

6. Wait for user input:
   - **"all"** or **"run all"**: Execute every recommendation
   - **Specific numbers** (e.g., "1, 3"): Execute only those
   - **"skip"**: Skip to Phase 3
   - **Custom instructions**: User may adjust scope or add context — respect it

## Phase 2: Fix

### Step 2.1 — Execute Selected Commands

Run each selected command in sequence against the source files:

1. Execute the command
2. After each command completes, output a one-line summary:
   ```
   /typeset — Fixed heading scale (h1-h4), increased body line-height to 1.6, added font-weight differentiation
   ```
3. Move to the next command

**Order matters**: Run structural fixes (`/arrange`, `/adapt`) before visual fixes (`/colorize`, `/typeset`) before polish (`/delight`, `/animate`). Reorder the user's selection if needed — explain why.

### Step 2.2 — Final Polish

After all selected commands complete, run **`/polish`** as the final pass. This catches small inconsistencies introduced by the individual fixes — rounding errors, minor spacing drift, transition timing mismatches.

### Step 2.3 — Summary

Output a brief change summary:

```
## Changes Applied

- /typeset: Rebuilt type scale (16/20/28/40px), set body line-height 1.6
- /colorize: Raised CTA contrast to 7.2:1, replaced secondary palette
- /polish: Normalized border-radius to 8px, aligned transition durations

Files modified: index.html, styles.css
```

## Phase 3: Verify

Ask the user:

```
Run another audit to verify improvements? Or done?
```

- **"yes"** / **"verify"** / **"audit again"**: Loop back to Phase 1. The new audit will show what improved and what remains.
- **"done"** / **"looks good"**: Complete the workflow.

Multiple loops are normal. The first pass catches the big issues; the second pass catches what the fixes introduced. Rarely need more than two loops.

## Rules

1. **Never fix without diagnosing first.** Phase 1 is not optional.
2. **Never skip user approval.** The recommendation list is a proposal, not a plan. Wait for explicit go-ahead.
3. **Respect .impeccable.md.** Every fix must align with the project's stated design context. A "fix" that violates the brand personality is not a fix.
4. **One command, one concern.** Do not let `/typeset` also fix colors. Each command stays in its lane.
5. **Summarize, don't narrate.** After each fix: one line. Save the details for the final summary.
6. **Structural before visual.** Layout and responsiveness first, then type and color, then motion and delight. Fixing color on a broken layout wastes effort.
