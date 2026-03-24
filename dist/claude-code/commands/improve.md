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

## Core (Impeccable)

### Step 1: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first.

### Step 2: Diagnose

Run on the target:

1. `/audit` — accessibility, performance, theming, responsive, anti-patterns
2. `/critique` — visual hierarchy, typography, color, spacing, emotional impact

Save both reports. Do not fix anything yet.

### Step 3: Recommend

See [_recommendation-loop.md](./_recommendation-loop.md) for the shared engine.

1. Map each finding to an Impeccable command
2. Group by command, order by severity
3. Check for conflicts (see Conflict Table below)
4. Present to user:

```
## Recommended Fixes

1. /typeset — 3 issues: weak heading scale, inconsistent weights, tight line-height
2. /colorize — 2 issues: low CTA contrast, monochrome sections
3. /arrange — 1 issue: uneven section spacing

⚠️ Note: /bolder + /clarify selected — bolder may increase visual weight that clarify tries to reduce. Will run /clarify last to preserve readability.

Run all? Or select which to apply:
```

Wait for user selection.

### Step 4: Fix

Run each selected command in the correct order:

**Execution order and rationale:**

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

### Step 5: Polish

Run `/polish` as the final pass. Always.

### Step 6: Verify

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

## Extras (conditional)

| Trigger | Extra |
|---------|-------|
| URL provided and Playwright available | Load live URL for visual verification between rounds |
| Before/after comparison requested | Desktop + mobile screenshots via Playwright |
| User says "commit" or "ship" | Stage and commit modified files |

---

## Rules

1. Never fix without diagnosing first
2. Never skip user approval on the recommendation list
3. Respect `.impeccable.md` — fixes must align with stated design context
4. One command, one concern — `/typeset` doesn't fix colors
5. Structure before visual before personality — always
6. Show progress between rounds — never re-audit silently
