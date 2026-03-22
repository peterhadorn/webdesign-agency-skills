---
name: full-treatment
description: "Run all Impeccable design commands in optimal order — full design treatment with before/after comparison"
---

# /full-treatment — Complete Impeccable Design Treatment

> Load + Guard → Baseline + Diagnose → Sequential Treatment with Check-ins → Results Comparison → Deploy/Commit

## Invocation

```
/full-treatment [url-or-file]

Accepts:
  - Live URL: https://example.com
  - Local file: src/index.html, app/page.tsx, etc.
```

---

## Phase 0: Load + Guard

### 0.1 Context Swap

Check whether `.impeccable.md` exists in the project root.
- If it exists: load it as the design context for all subsequent commands.
- If missing: run `/teach-impeccable` first to generate it, then proceed.

### 0.2 Load Target

- **URL**: Load via Playwright. Wait for network idle.
- **Local file**: Open via Playwright (`file://` protocol) or the appropriate dev server.

If the page fails to render (timeout, 404, JS crash): report the error and **ABORT**.

### 0.3 Before Screenshots

Take baseline screenshots at two viewports:
- **Desktop**: 1440px width
- **Mobile**: 375px width

Save as reference for Phase 3 comparison.

---

## Phase 1: Diagnose

### 1.1 Run /audit

Run the Impeccable `/audit` command on the rendered page. Save ALL scores and findings as the baseline. This serves double duty: baseline metrics AND the diagnostic findings report that drives smart-skip logic in Phase 2.

### 1.2 Run /critique

Run the Impeccable `/critique` command for a full UX critique. Save all findings categorized by issue type.

### 1.3 Present Combined Findings

Summarize the combined findings from `/audit` and `/critique`:

```
## Diagnosis: [target]

### Audit Scores (Baseline)
- Accessibility: [score]
- Performance: [score]
- Anti-patterns: [pass/fail]
- Issues found: [N]

### Critique Highlights
- [Top 3-5 most impactful issues, grouped by category]

### Treatment Plan
- Steps that will run: [list based on findings]
- Steps that will be skipped: [list with reason]

Starting full treatment. I'll check in after each step.
```

---

## Phase 2: Treatment (Sequential, with Check-ins)

Run each step in order. Between every step, pause for the user.

### Treatment Order

The order is deliberate: **structure before style, resilience before personality, polish last.**

<!--
Rationale:
1.  distill   — strip complexity first (reduces work for all subsequent steps)
2.  arrange   — fix spatial structure (layout must be correct before styling)
3.  typeset   — fix typography hierarchy (depends on clean layout)
4.  colorize  — add strategic color (depends on typography being set)
5.  normalize — align to design system (reconcile after structural changes)
6.  clarify   — fix copy/labels (content depends on structure being stable)
7.  onboard   — empty states, first-time UX (content-dependent)
8.  harden    — error handling, edge cases (functional layer)
9.  adapt     — responsive breakpoints (must come after layout/typography/color)
10. optimize  — performance (don't optimize until design is stable)
11. animate   — purposeful motion (add after layout is final)
12. delight   — moments of joy (personality layer, near-end)
13. bolder/quieter — intensity adjustment (near-final calibration)
14. overdrive — technically ambitious effects (optional, after everything else works)
15. polish    — always last (final sweep catches anything remaining)
-->

| Step | Command | After completion, say: |
|------|---------|------------------------|
| 1 | `/distill` | "Stripped [X] unnecessary elements. Continue?" |
| 2 | `/arrange` | "Fixed layout and spacing. Continue?" |
| 3 | `/typeset` | "Improved typography hierarchy. Continue?" |
| 4 | `/colorize` | "Added strategic color. Continue?" |
| 5 | `/normalize` | "Aligned to design system. Continue?" |
| 6 | `/clarify` | "Improved copy and labels. Continue?" |
| 7 | `/onboard` | "Improved empty/first-time states. Continue?" |
| 8 | `/harden` | "Added error handling for edge cases. Continue?" |
| 9 | `/adapt` | "Fixed responsive issues. Continue?" |
| 10 | `/optimize` | "Improved performance. Continue?" |
| 11 | `/animate` | "Added purposeful motion. Continue?" |
| 12 | `/delight` | "Added personality and delight. Continue?" |
| 13 | `/bolder` OR `/quieter` | Ask the user which direction, or offer to skip |
| 14 | `/overdrive` | "Added technically ambitious effects. Continue?" (or skip) |
| 15 | `/polish` | "Final polish pass complete." |

### Check-in Behavior

After each step, wait for the user. They can respond:

| Response | Action |
|----------|--------|
| `y`, `yes`, `continue` | Proceed to the next step |
| `skip` | Skip the current step (if not yet run) or the next step |
| `stop` | Halt the treatment, jump directly to Phase 3 (Results) |
| Specific feedback | Address the feedback, then ask "Continue?" again |
| A command name (e.g., `/colorize`) | Force-run that specific step, even if it was going to be skipped |

### Smart Skip Logic

Before each step, check whether BOTH `/audit` AND `/critique` found issues in that step's category. If neither diagnostic found relevant issues for a category, announce the skip:

> "No [category] issues found in audit or critique — skipping /[command]. Type `/[command]` to force-run."

The user can always override a skip by typing the command name.

### Finding-to-Category Mapping

| Step | Command | Audit/Critique Category |
|------|---------|------------------------|
| 1 | `/distill` | Over-engineered, unnecessary complexity |
| 2 | `/arrange` | Layout/spacing issues |
| 3 | `/typeset` | Typography issues |
| 4 | `/colorize` | Color/contrast issues |
| 5 | `/normalize` | Design system inconsistency |
| 6 | `/clarify` | Copy/label clarity |
| 7 | `/onboard` | Onboarding/empty states |
| 8 | `/harden` | Error handling/edge cases |
| 9 | `/adapt` | Responsive breakpoints |
| 10 | `/optimize` | Performance issues |
| 11 | `/animate` | Motion/animation gaps |
| 12 | `/delight` | Missing delight/personality |
| 13 | `/bolder` | Too bland/safe |
| 13 | `/quieter` | Too noisy/aggressive |
| 14 | `/overdrive` | Technically ambitious effects |
| 15 | `/polish` | ALWAYS runs — never skipped |

### Step 13 Special Handling

Step 13 requires a direction choice. Present:

> "Step 13: Intensity adjustment. Options:
> - `/bolder` — make the design more confident and striking
> - `/quieter` — tone down noise, reduce visual intensity
> - `skip` — leave intensity as-is
>
> Which direction?"

### Step 14 Special Handling

Step 14 (`/overdrive`) is optional and adds technically ambitious effects (advanced CSS, canvas, WebGL, etc.). Before running:

> "Step 14: /overdrive adds technically ambitious effects. This is optional and may increase complexity. Run it? (y/skip)"

---

## Phase 3: Results

### 3.1 Post-Treatment Audit

Run `/audit` again on the treated page. Record all scores.

### 3.2 After Screenshots

Take screenshots at the same viewports as Phase 1:
- **Desktop**: 1440px width
- **Mobile**: 375px width

### 3.3 Present Comparison

```markdown
## Full Treatment Results: [target]

| Metric         | Before | After | Delta |
|----------------|--------|-------|-------|
| A11y score     | [X]    | [Y]   | [+/-] |
| Performance    | [X]    | [Y]   | [+/-] |
| Anti-patterns  | [P/F]  | [P/F] |       |
| Issues found   | [N]    | [M]   | [-Z]  |

### Steps Applied
[numbered list of steps that ran]

### Steps Skipped
[list with reason: "no issues found" or "user skipped" or "user stopped"]

### Before vs After
Desktop: [before screenshot] vs [after screenshot]
Mobile:  [before screenshot] vs [after screenshot]
```

---

## Phase 4: Deploy (if applicable)

### 4.1 Local Files

If working on local source files, offer to commit the changes:

> "Treatment complete. Commit changes?"

Wait for explicit user approval before committing.

### 4.2 Live Site

If working against a live URL, note that changes were made to local source files only:

> "Changes applied to local source files. Deploy to your hosting environment when ready."

---

## Commands NOT in the Treatment Sequence

These Impeccable commands are used outside the 15-step treatment and should not be confused with treatment steps:

| Command | Role | When Used |
|---------|------|-----------|
| `/audit` | Diagnostic input | Phase 1 (baseline) and Phase 3 (comparison) |
| `/critique` | Diagnostic input | Phase 1 (findings report) |
| `/teach-impeccable` | One-time setup | Phase 0 (if design context missing) |
| `/frontend-design` | Full page builds | Used for complete rebuilds, not incremental treatment |
| `/extract` | Component extraction | Post-treatment if needed, not part of the quality pass |
