# Impeccable Workflows

Orchestration layer for [Impeccable](https://github.com/pbakaus/impeccable). Chains Impeccable's 20 design commands into structured workflows with a shared recommendation engine.

## What This Is

Impeccable gives you 20 design commands (`/audit`, `/critique`, `/typeset`, `/colorize`, etc.). These workflows handle the orchestration: which commands to run, in what order, how to synthesize findings, and how to present results.

Two self-contained skills. Plain Markdown — no runtime, no dependencies.

## Skills

### `/prospect-audit`

Analyze any URL and generate a business-language analysis. Runs `/audit` + `/critique`, then translates technical findings into language a business owner actually cares about. Works for sales prospecting, self-audits, client reporting, and competitive analysis.

```
/prospect-audit https://example.com
```

Output sections:
- **What's Costing You Customers** — problems framed as lost business, not technical jargon
- **What We'd Fix** — improvements framed as outcomes
- **What Caught Our Eye** — genuine positives that prove you looked
- **Technical Details** — raw audit data (internal, not for the client)

Adapts to the site's language automatically.

**Example output** (from a real audit of a cleaning company website):

````
## Website Analysis: example-cleaning.ch

### What's Costing You Customers
- Your scroll animations are broken — visitors see a static page instead
  of the polished experience you designed. A technical error is blocking
  all motion effects.
- Google shows no description under your link in search results. Your
  competitors have an inviting sentence there. You're losing clicks.
- When someone shares your link on WhatsApp, the preview is blank — no
  image, no text. Looks unprofessional and gets clicked less.

### What We'd Fix
- Make Google show your business properly — add a description and preview
  image so every search result looks professional.
- Fix the broken animations — one technical correction restores all the
  motion effects across the site.
- Make your images visible to Google — right now Google can't read 7 of
  your 8 images. That's lost visibility for local searches.

### What Caught Our Eye
- The green/purple color scheme stands out from typical cleaning company
  sites — that's a real advantage.
- "In the beautiful Glarnerland" in the headline — strong local connection
  that works well for local search.
- Phone number is prominent and clickable — many businesses get this wrong.

### Technical Details (internal)
- Fonts: DM Sans, Urbanist
- 10 JS console errors (jQuery conflict)
- 7/8 images missing alt text
- No meta description, no OG tags, no Schema.org
- Load time: 2.5s
````

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

## Installation

### Claude Code

```bash
cp -r dist/claude-code/commands/* ~/.claude/commands/
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

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Impeccable](https://github.com/pbakaus/impeccable) installed as a Claude Code plugin
- At least one browser MCP server (both recommended):

| Server | What it does | Install |
|--------|-------------|---------|
| **Playwright MCP** | Headless browser — fast automated page loading and inspection | `claude mcp add playwright -- npx @playwright/mcp@latest` |
| **Chrome DevTools** | Controls your real browser — sees cookies, geo content, logged-in states | `claude plugin add superpowers-chrome` |

The skills will detect available browser tools on first run and guide you through setup if needed.

## How It Works

These are Markdown skill files — structured instructions that tell the AI to invoke Impeccable commands in sequence with synthesis logic between steps. No runtime, no build step. The AI handles rendering, command execution, finding synthesis, and result presentation.

## License

MIT
