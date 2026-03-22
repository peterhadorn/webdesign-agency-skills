---
name: compare
description: "Compare two websites or files side by side — audit scores, design quality, and specific differences"
---

# /compare — Side-by-Side Comparison

Audit two targets and present a structured comparison.

```
/compare [a] [b]
```

Targets can be URLs, file paths, or a mix.

**Use cases:** Your site vs competitor, before vs after, two design approaches, client's site vs your redesign.

---

## Core (Impeccable)

### Step 1: Context

Check `.impeccable.md` at project root. If missing, ask which target (if either) is "yours" and run `/teach-impeccable` on it.

### Step 2: Diagnose Both

Run independently on each target:

**Target A:**
1. `/audit` — save findings
2. `/critique` — save findings

**Target B:**
1. `/audit` — save findings
2. `/critique` — save findings

### Step 3: Compare

```markdown
## Comparison: [A] vs [B]

### Score Comparison

| Metric | [A] | [B] | Winner |
|--------|-----|-----|--------|
| Accessibility | X | Y | → |
| Performance | X | Y | → |
| Anti-patterns | X | Y | → |
| Typography | X | Y | → |
| Color/contrast | X | Y | → |
| Mobile | X | Y | → |

### Where [A] Wins
- [Specific advantages with detail]

### Where [B] Wins
- [Specific advantages with detail]

### Key Differences
- [Differences that are taste, not quality]

### Recommendation
[1-2 sentences: which is stronger overall and why]
```

### Rules

1. Be specific: "1.2s vs 4.8s load" not "A is faster"
2. Don't force a winner — use "Tie" when genuinely equal
3. Distinguish taste (subjective) from quality (objective)
4. Reference actual content by name
5. Both targets get equal scrutiny

---

## Optional Extensions

- **Playwright rendering** — Load live URLs, take desktop + mobile screenshots of both
- **Visual comparison** — Side-by-side screenshot grid
- **SEO comparison** — Title, meta, schema, heading structure for both
- **Performance comparison** — Load times, resource counts, Core Web Vitals estimates

---

## Next Steps

| Context | Offer |
|---------|-------|
| Your site vs competitor | "Run `/improve` to close the gaps?" |
| Before vs after | Summarize improvements and regressions |
| Two approaches | Recommend which to proceed with |
