---
name: full-treatment
description: "Run all Impeccable design commands in optimal order — full design treatment with before/after comparison"
---

# /full-treatment — Complete Impeccable Design Treatment

Run all 15 treatment commands in optimal order with smart skip and check-ins.

```
/full-treatment [url-or-file]
```

---

## Core (Impeccable)

### Step 1: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first.

### Step 2: Diagnose

1. `/audit` — save scores as baseline + findings for smart skip
2. `/critique` — save findings for smart skip

Present combined summary:

```
## Diagnosis

Audit: [scores]
Critique: [top issues]

Steps that will run: [list]
Steps that will skip: [list with reason]

Starting treatment.
```

### Step 3: Treatment

15 steps in order. **Structure before style, resilience before personality, polish last.**

| Step | Command | After completion |
|------|---------|-----------------|
| 1 | `/distill` | "Stripped [X]. Continue?" |
| 2 | `/arrange` | "Fixed layout/spacing. Continue?" |
| 3 | `/typeset` | "Improved typography. Continue?" |
| 4 | `/colorize` | "Added strategic color. Continue?" |
| 5 | `/normalize` | "Aligned to design system. Continue?" |
| 6 | `/clarify` | "Improved copy/labels. Continue?" |
| 7 | `/onboard` | "Improved empty states. Continue?" |
| 8 | `/harden` | "Added error handling. Continue?" |
| 9 | `/adapt` | "Fixed responsive issues. Continue?" |
| 10 | `/optimize` | "Improved performance. Continue?" |
| 11 | `/animate` | "Added motion. Continue?" |
| 12 | `/delight` | "Added personality. Continue?" |
| 13 | `/bolder` OR `/quieter` | Ask direction, or skip |
| 14 | `/overdrive` | Optional — ask before running |
| 15 | `/polish` | "Final pass complete." (ALWAYS runs) |

**Check-ins:** After each step, user responds:
- `y` / `continue` → next step
- `skip` → skip this step
- `stop` → jump to results
- Feedback → address it, then continue
- Command name → force-run a skipped step

**Smart skip:** If BOTH audit AND critique found zero issues for a step's category, auto-skip:
> "No typography issues found — skipping /typeset. Type `/typeset` to force-run."

Category mapping: see [_recommendation-loop.md](./_recommendation-loop.md)

### Step 4: Results

Run `/audit` again. Compare:

```
## Results

| Metric | Before | After | Delta |
|--------|--------|-------|-------|
| A11y   | [X]    | [Y]   | [+/-] |
| Perf   | [X]    | [Y]   | [+/-] |
| Issues | [N]    | [M]   | [-Z]  |

Steps applied: [list]
Steps skipped: [list]
```

---

## Optional Extensions

- **Playwright rendering** — Load live URL, take before/after screenshots at 1440px + 375px
- **Visual comparison** — Side-by-side desktop + mobile screenshots
- **Commit changes** — Stage and commit after treatment

---

## Commands NOT in Treatment

| Command | Role |
|---------|------|
| `/audit` | Diagnostic (Step 2 + Step 4) |
| `/critique` | Diagnostic (Step 2) |
| `/teach-impeccable` | One-time setup |
| `/frontend-design` | Full rebuilds, not incremental |
| `/extract` | Post-treatment refactoring |
