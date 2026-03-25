# Web Design Agency Skills

Two Claude Code skills for web design agencies. Audit any website and get a client-ready sales brief, or run a targeted improvement loop that diagnoses, recommends, and fixes design issues.

Built on [Impeccable](https://github.com/pbakaus/impeccable)'s 20 design commands. These skills handle the orchestration: which commands to run, in what order, and how to translate findings into language clients actually understand.

## Skills

### `/prospect-audit`

Analyze any URL and generate a business-language analysis. Runs `/audit` + `/critique`, then translates technical findings into language a business owner actually cares about. Works for sales prospecting, self-audits, client reporting, and competitive analysis.

```
/prospect-audit https://example.com
```

Output sections:
- **What's Costing You Customers:** problems framed as lost business, not technical jargon
- **What We'd Fix:** improvements framed as outcomes
- **What Caught Our Eye:** genuine positives that prove you looked
- **Technical Details:** raw audit data (internal, not for the client)

Adapts to the site's language automatically.

**Example output** (from a real audit of a cleaning company website):

````
## Website Analysis: example-cleaning.ch

### What's Costing You Customers
- Your scroll animations are broken. Visitors see a static page instead
  of the polished experience you designed. A technical error is blocking
  all motion effects.
- Google shows no description under your link in search results. Your
  competitors have an inviting sentence there. You're losing clicks.
- When someone shares your link on WhatsApp, the preview is blank. No
  image, no text. Looks unprofessional and gets clicked less.

### What We'd Fix
- Make Google show your business properly. Add a description and preview
  image so every search result looks professional.
- Fix the broken animations. One technical correction restores all the
  motion effects across the site.
- Make your images visible to Google. Right now Google can't read 7 of
  your 8 images. That's lost visibility for local searches.

### What Caught Our Eye
- The green/purple color scheme stands out from typical cleaning company
  sites. That's a real advantage.
- "In the beautiful Glarnerland" in the headline. Strong local connection
  that works well for local search.
- Phone number is prominent and clickable. Many businesses get this wrong.

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

## Examples

Real `/prospect-audit` output from live websites:

| Site | What it shows |
|------|---------------|
| [stripe.com](examples/stripe.md) | Enterprise SaaS, strong brand, accessibility gaps |
| [craigslist.org](examples/craigslist.md) | Famously minimal, dated design vs. deliberate simplicity |
| [webevolve.ch](examples/webevolve.md) | Self-audit, testing the tool on our own site |
| [spacex.com](examples/spacex.md) | Visual-first brand, hidden navigation, no contact path |
| [subway.com](examples/subway.md) | Fast food chain, promotion overload, decision fatigue |
| [wellsfargo.com](examples/wellsfargo.md) | Banking, competing priorities, new vs. existing customers |

## Installation

### Claude Code

```bash
cp -r dist/claude-code/commands/* ~/.claude/commands/
```

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Impeccable](https://github.com/pbakaus/impeccable) installed as a Claude Code plugin
- At least one browser MCP server (both recommended):

| Server | What it does | Install |
|--------|-------------|---------|
| **Playwright MCP** | Headless browser, fast automated page loading and inspection | `claude mcp add playwright -- npx @playwright/mcp@latest` |
| **Chrome DevTools** | Controls your real browser, sees cookies, geo content, logged-in states | `claude plugin add superpowers-chrome` |

The skills will detect available browser tools on first run and guide you through setup if needed.

**Optional but recommended:** Run `/teach-impeccable` once per project to create a `.impeccable.md` design context file. This gives Impeccable your brand, audience, and aesthetic direction. Audits and fixes become more relevant. The skills work without it, but results are better with it.

## How It Works

These are Markdown skill files: structured instructions that tell the AI to invoke Impeccable commands in sequence with synthesis logic between steps. No runtime, no build step. The AI handles rendering, command execution, analysis, and result presentation.

## License

MIT
