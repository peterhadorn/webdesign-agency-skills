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

## Step 1: Load Both

- **URLs** — Navigate via Playwright to render each page
- **Files** — Read each file into context
- If either fails: report which and abort

## Step 2: Context

Check `.impeccable.md` at project root. If missing, ask which target is "yours" and run `/teach-impeccable` on it.

## Step 3: Diagnose Both

Run independently on each target:

**Target A:**
1. `/audit`
2. `/critique`

**Target B:**
1. `/audit`
2. `/critique`

## Step 4: Compare

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
[1-2 sentences: which is stronger and why]
```

### Rules

1. Be specific: "1.2s vs 4.8s load" not "A is faster"
2. Don't force a winner — use "Tie" when genuinely equal
3. Distinguish taste (subjective) from quality (objective)
4. Reference actual content by name
5. Both targets get equal scrutiny

## Step 5: Next Steps

| Context | Offer |
|---------|-------|
| Your site vs competitor | "Run `/improve` to close the gaps?" |
| Before vs after | Summarize improvements and regressions |
| Two approaches | Recommend which to proceed with |

---

## Optional Extensions

- **Screenshots** — Desktop + mobile of both targets via Playwright
- **SEO comparison** — Title, meta, schema, heading structure for both
- **Performance comparison** — Load times, resource counts
