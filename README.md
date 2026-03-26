# Web Design Agency Skills

Five Claude Code skills for web design agencies. Audit any website, get a client-ready sales brief, run a targeted improvement loop, achieve perfect Lighthouse scores, deep-dive into Core Web Vitals, or test responsive behavior across every breakpoint.

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

**Score: 4/10** — Solid local identity, but broken animations, missing SEO basics,
and invisible images are costing you search traffic and trust.

### What's Costing You Customers
- Your scroll animations are broken. Visitors see a static page instead
  of the polished experience you designed. A technical error is blocking
  all motion effects.
- Google shows no description under your link in search results. Your
  competitors have an inviting sentence there. You're losing clicks.
- When someone shares your link on WhatsApp, the preview is blank. No
  image, no text. Looks unprofessional and gets clicked less.

### What We'd Fix (in priority order)
1. Fix the broken animations. One technical correction restores all the
   motion effects across the site. · _Quick win_
2. Make Google show your business properly. Add a description and preview
   image so every search result looks professional. · _Quick win_
3. Make your images visible to Google. Right now Google can't read 7 of
   your 8 images. That's lost visibility for local searches. · _Quick win_

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

### `/lighthouse-100`

Automated loop that gets every Lighthouse category to 100. Audits, parses every failing check, fixes it, and re-runs until Accessibility, Best Practices, and SEO all hit 100/100/100 — on both mobile and desktop.

```
/lighthouse-100 https://example.com
```

1. Runs Lighthouse audit (mobile first)
2. Parses all failed audits from the JSON report
3. Fixes each failure using built-in lookup tables (accessibility, best practices, SEO)
4. Rebuilds and re-audits until all scores hit 100
5. Repeats for desktop
6. Reports every fix with before/after scores

### `/performance-audit`

Core Web Vitals deep dive. Goes beyond a Lighthouse Performance score — measures LCP, CLS, INP with element-level attribution, diagnoses the root cause, and applies targeted fixes.

```
/performance-audit https://example.com
```

1. Runs Lighthouse + performance trace + network analysis
2. Records baseline metrics (LCP, CLS, INP, FCP, TTFB, Speed Index, TBT)
3. Diagnoses each failing metric to its root cause (specific element, specific resource)
4. Fixes in priority order: delivery → critical path → assets → layout stability → interactivity
5. Re-measures and compares to baseline

### `/responsive-check`

Tests a page across 8 breakpoints (320px–1920px). Screenshots each, detects layout breaks, and fixes them.

```
/responsive-check https://example.com
```

1. Screenshots at Mobile S/M/L, Tablet Portrait/Landscape, Desktop, Desktop L, Ultrawide
2. Analyzes each for overflow, overlaps, cut-off content, tiny touch targets, unreadable text
3. Reports issues grouped by severity with screenshot evidence
4. Fixes with targeted CSS + runs `/adapt` for systematic responsive cleanup
5. Re-screenshots to verify

## Examples

Real `/prospect-audit` output from live websites:

| Site | What it shows |
|------|---------------|
| [stripe.com](examples/stripe.md) | Enterprise SaaS, strong brand, accessibility gaps |
| [craigslist.org](examples/craigslist.md) | Famously minimal, dated design vs. deliberate simplicity |
| [spacex.com](examples/spacex.md) | Visual-first brand, hidden navigation, no contact path |
| [subway.com](examples/subway.md) | Fast food chain, promotion overload, decision fatigue |
| [ubs.com](examples/ubs.md) | Global wealth management, brochure homepage, broken icon fonts |
| [wellsfargo.com](examples/wellsfargo.md) | Banking, competing priorities, new vs. existing customers |

## Installation

```bash
# Global (all projects)
git clone https://github.com/peterhadorn/webdesign-agency-skills.git && cp -r webdesign-agency-skills/dist/claude-code/commands/* ~/.claude/commands/ && rm -rf webdesign-agency-skills

# Project-specific
git clone https://github.com/peterhadorn/webdesign-agency-skills.git && cp -r webdesign-agency-skills/dist/claude-code/commands/* .claude/commands/ && rm -rf webdesign-agency-skills
```

Or just tell Claude Code: "Clone peterhadorn/webdesign-agency-skills and copy the skills to my commands folder."

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

Apache 2.0
