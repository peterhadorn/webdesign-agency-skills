# Impeccable Workflows

Orchestration layer for [Impeccable](https://github.com/pbakaus/impeccable). Chains Impeccable's 20 design commands into structured workflows with a shared recommendation engine.

## What This Is

Impeccable gives you 20 design commands (`/audit`, `/critique`, `/typeset`, `/colorize`, etc.). These workflows handle the orchestration: which commands to run, in what order, how to synthesize findings, and how to present results.

Three skills. One shared engine. Plain Markdown — no runtime, no dependencies.

## Skills

### `/prospect-audit`

Analyze any URL and generate a brief for the site owner. Runs `/audit` + `/critique`, then translates technical findings into business language.

```
/prospect-audit https://example.com
```

Output sections:
- **What's Costing You Customers** — problems framed as lost business, not technical jargon
- **What We'd Fix** — improvements framed as outcomes
- **What Caught Our Eye** — genuine positives that prove you looked
- **Technical Details** — raw audit data (internal, not for the client)

Adapts to the site's language automatically.

### `/full-treatment`

Run all 15 Impeccable commands in optimal order with before/after comparison.

```
/full-treatment https://example.com
```

| Step | Command | What It Fixes |
|------|---------|---------------|
| 1 | `/distill` | Strip unnecessary complexity |
| 2 | `/arrange` | Layout and spacing |
| 3 | `/typeset` | Typography hierarchy |
| 4 | `/colorize` | Strategic color |
| 5 | `/normalize` | Design system alignment |
| 6 | `/clarify` | Copy and label clarity |
| 7 | `/onboard` | Empty states, first-time UX |
| 8 | `/harden` | Error handling, edge cases |
| 9 | `/adapt` | Responsive breakpoints |
| 10 | `/optimize` | Performance |
| 11 | `/animate` | Purposeful motion |
| 12 | `/delight` | Personality |
| 13 | `/bolder` or `/quieter` | Intensity calibration |
| 14 | `/overdrive` | Technically ambitious effects (optional) |
| 15 | `/polish` | Final sweep (always runs) |

Order is deliberate: structure before style, resilience before personality, polish last.

**Smart skip**: Steps auto-skip when audit + critique found zero issues in that category. Force-run any step by typing the command name.

**Check-ins**: Pauses after each step. Continue, skip, stop, or give feedback.

### `/improve`

Targeted improvement loop. Diagnose, recommend, fix only what's needed.

```
/improve https://example.com
```

1. Runs `/audit` + `/critique`
2. Maps findings to Impeccable commands
3. Presents grouped recommendations ordered by severity
4. You pick which to run
5. Runs selected commands, then `/polish`
6. Offers to re-check with another audit

## The Recommendation Loop

Shared engine across all three skills.

```
/audit          → technical findings
/critique       → UX assessment
Synthesize      → deduplicate, merge findings
Map             → assign each finding to a command
Group + order   → cluster by command, sort by severity
Present         → user picks which to run
Execute         → run selected, then /polish
Re-check        → verify with another audit (optional)
```

### Finding-to-Command Mapping

| Finding | Command |
|---------|---------|
| Over-engineered | `/distill` |
| Layout/spacing | `/arrange` |
| Typography | `/typeset` |
| Color/contrast | `/colorize` |
| Design system inconsistency | `/normalize` |
| Copy/label clarity | `/clarify` |
| Onboarding/empty states | `/onboard` |
| Error handling/edge cases | `/harden` |
| Responsive breakpoints | `/adapt` |
| Performance | `/optimize` |
| Motion/animation gaps | `/animate` |
| Missing personality | `/delight` |
| Too bland/safe | `/bolder` |
| Too noisy/aggressive | `/quieter` |
| Technically ambitious | `/overdrive` |

## Installation

### Claude Code

```bash
cp -r dist/claude-code/commands/* ~/.claude/commands/
```

### Cursor

```bash
cp -r dist/cursor/.cursor/skills/* your-project/.cursor/skills/
```

### Gemini CLI

```bash
cp -r dist/gemini/.gemini/skills/* your-project/.gemini/skills/
```

## Multi-Surface Context

Impeccable reads `.impeccable.md` at the project root for design context. If your project has multiple design surfaces (marketing site, dashboard, docs), maintain separate context files and swap before running commands.

```
config/
  marketing.impeccable.md
  dashboard.impeccable.md
  docs.impeccable.md
```

```bash
cp config/dashboard.impeccable.md .impeccable.md
# Now all commands run with dashboard context
```

Add `.impeccable.md` to `.gitignore` — it's a transient working file.

See [docs/CONTEXT-SWAP.md](docs/CONTEXT-SWAP.md) for details.

## Example Contexts

Pre-built `.impeccable.md` templates in `config/examples/`:

| Template | For |
|----------|-----|
| `saas-dashboard.md` | Data-dense admin panels |
| `marketing-site.md` | Landing pages, hero sections |
| `docs-site.md` | Technical documentation |
| `ecommerce.md` | Product pages, checkout flows |

Run `/teach-impeccable` on your actual pages for a tailored context, or start from these templates.

## Requirements

- [Impeccable](https://github.com/pbakaus/impeccable) installed
- Playwright or Chrome DevTools MCP server (for page rendering)
- Claude Code, Cursor, or Gemini CLI

## How It Works

These are Markdown skill files — structured instructions that tell the AI to invoke Impeccable commands in sequence with synthesis logic between steps. No runtime, no build step. The AI handles rendering, command execution, finding synthesis, and result presentation.

## License

MIT
