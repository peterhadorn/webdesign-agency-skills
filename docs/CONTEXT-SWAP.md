# Multi-Surface Context Swapping

Impeccable skills require a `.impeccable.md` file at your project root with a `## Design Context` block. But many projects have multiple design surfaces that need different contexts — a marketing site, an admin dashboard, and a docs site don't share the same design principles.

## The Problem

Impeccable reads ONE `.impeccable.md` at the project root. If your project has 3 surfaces, you need to swap the right context before running any Impeccable command.

## The Solution

1. **Store context files per surface** in `config/examples/` or any organized location:

```
config/
├── marketing.impeccable.md
├── dashboard.impeccable.md
└── docs.impeccable.md
```

2. **Swap before running commands.** Before any `/audit`, `/critique`, `/typeset`, etc.:

```bash
cp config/marketing.impeccable.md .impeccable.md
```

3. **The workflow skills handle this automatically.** When using `/prospect-audit` or `/improve`, the skill checks for context and swaps or prompts you to create one.

## Creating Context

Run `/teach-impeccable` once per surface. It asks about your users, brand, and aesthetic direction, then writes `.impeccable.md`. Copy the result to your config directory for future use.

## Example Setup

```
my-saas-project/
├── .impeccable.md              ← runtime (swapped per surface, gitignored)
├── .gitignore                  ← includes .impeccable.md
├── config/
│   ├── marketing.impeccable.md ← bright, bold, conversion-focused
│   ├── dashboard.impeccable.md ← dark, data-dense, utilitarian
│   └── docs.impeccable.md      ← clean, readable, code-friendly
├── marketing/                  ← marketing site source
├── app/                        ← dashboard source
└── docs/                       ← documentation source
```

## Pre-Built Templates

See `config/examples/` for ready-to-use context files:

- **saas-dashboard.md** — Dark theme, data density, keyboard-friendly
- **marketing-site.md** — Bold, distinctive, trust-focused
- **docs-site.md** — Clean, scannable, code-first
- **ecommerce.md** — Product-focused, trust signals, fast checkout
