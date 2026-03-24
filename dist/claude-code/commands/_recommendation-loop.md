# Finding-to-Command Mapping & Recommendation Loop

Shared reference used by `/improve` and `/prospect-audit`.

## Finding-to-Command Mapping

Use this table to map `/audit` and `/critique` findings to the correct Impeccable command.

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

Some findings could map to multiple commands. Use these tiebreakers:

| Finding | Seems like | Actually | Why |
|---------|-----------|----------|-----|
| "Buttons look different on every page" | `/colorize` | `/normalize` | It's a consistency problem, not a color problem |
| "Too much whitespace" | `/arrange` | `/distill` if elements are sparse, `/arrange` if spacing is wrong | Check whether the issue is content density or spacing values |
| "Text is hard to read" | `/typeset` | `/colorize` if contrast is the issue, `/typeset` if scale/weight is | Check what specifically makes it hard to read |
| "Page feels slow" | `/optimize` | `/animate` if it's perceived speed (no loading indicators), `/optimize` if measured | Check whether the problem is actual or perceived performance |

## Recommendation Loop Steps

After running `/audit` and `/critique`, apply this synthesis process:

1. **Read** both the audit and critique reports
2. **Map** each finding to an Impeccable command using the table above
3. **Deduplicate** — if audit and critique both flag the same issue, merge into one finding
4. **Group** findings by command — if three issues all need `/typeset`, they become one item
5. **Order** by severity: critical issues first, polish last
6. **Present** the recommendation list to the user:

```
## Recommended Fixes (from audit + critique)

1. /typeset — 3 issues: heading scale inconsistent, body line-height too tight, font weights not differentiated
2. /colorize — 2 issues: CTA contrast below 4.5:1, secondary palette muddy against background
3. /arrange — 1 issue: card grid breaks at tablet widths, uneven gutter spacing

Run all? Or select which to apply (e.g., "1 and 3", "skip 2"):
```

7. **Wait for user input:**
   - **"all"** or **"run all"**: Execute every recommendation
   - **Specific numbers** (e.g., "1, 3"): Execute only those
   - **"skip"**: Skip fixes entirely
   - **Custom instructions**: User may adjust scope or add context — respect it

8. **Execute** selected commands in sequence. **Order matters**: structure → systems → visual → personality (see `/improve` Step 4 for the full phase table). Reorder the user's selection if needed — explain why.

9. **Polish**: After all selected commands complete, run `/polish` as the final pass.

10. **Re-check** (optional): Offer to run `/audit` again to verify. Show what changed between rounds — never re-audit silently.
