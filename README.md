# Impeccable Workflows

> Orchestration layer for [Impeccable](https://github.com/pbakaus/impeccable) -- chain 20 design commands into structured workflows.

**Turn any website into a sales brief in 60 seconds.**

Impeccable gives you 20 powerful design commands. But knowing *which* to run, in *what order*, and how to *synthesize the findings* into something actionable -- that's orchestration. That's what this repo provides.

Three skills. One shared engine. Works with Claude Code, Cursor, and Gemini CLI.

---

## Quick Demo

Point `/prospect-audit` at any URL:

```
/prospect-audit https://example-dental-practice.com
```

60 seconds later, you have this:

```markdown
## Website Analysis: example-dental-practice.com

### What's Costing You Customers
- Your site takes 8 seconds to load on mobile -- 53% of visitors leave
  before they see your phone number.
- Google can't read your images. You're invisible for searches like
  "dentist near me" while competitors show up with rich results.
- The contact form is broken on iPhone. Every failed submission is a
  patient who calls someone else.

### What We'd Fix
- Cut load time to under 2 seconds -- keep visitors long enough to book.
- Make every image visible to Google -- show up in local searches.
- Fix the mobile contact flow -- turn website visitors into appointments.

### What Caught Our Eye
- The patient testimonials section is well-placed and builds real trust.
- Phone number is prominent and clickable -- many practices get this wrong.
- The "Our Team" photos feel genuine, not stock. That matters.

### Technical Details (internal -- do NOT send to client)
- Audit score: Accessibility 34/100, Performance 22/100
- 7/8 images missing alt text
- 10 JS console errors (jQuery conflict breaks scroll animations)
- No meta description, title tag is "Home"
- Contact form missing error states on all fields
```

The top three sections are written for the business owner. No jargon, no WCAG references, no pixel counts. Just lost customers and clear fixes. The technical section stays internal for your team.

---

## Skills

### `/prospect-audit` -- Sales Intelligence from Any URL

The star of the show. Point it at a prospect's website and get a business-language analysis ready for outreach.

**What it does:**
1. Renders the page via Playwright
2. Runs Impeccable's `/audit` (technical) and `/critique` (UX)
3. Translates findings into business language
4. Outputs a brief framed for the site owner, not a developer

**Who it's for:** Freelancers, agencies, and anyone doing web design sales. Run it before a cold email, before a sales call, or as part of your prospecting workflow.

**Output format:**
- **What's Costing You Customers** -- 2-3 problems framed as lost business
- **What We'd Fix** -- 3-5 improvements framed as outcomes, not tasks
- **What Caught Our Eye** -- 3-4 genuine positives proving you actually looked
- **Technical Details** -- raw audit data for your internal use

Every finding answers one question: *"What does this cost me in customers or money?"*

---

### `/full-treatment` -- Complete Design Overhaul

Run all 15 Impeccable commands in optimal order with before/after scoring.

**The order is deliberate:** structure before style, resilience before personality, polish last.

| Step | Command | Category |
|------|---------|----------|
| 1 | `/distill` | Strip unnecessary complexity |
| 2 | `/arrange` | Fix layout and spacing |
| 3 | `/typeset` | Typography hierarchy |
| 4 | `/colorize` | Strategic color |
| 5 | `/normalize` | Design system alignment |
| 6 | `/clarify` | Copy and label clarity |
| 7 | `/onboard` | Empty states, first-time UX |
| 8 | `/harden` | Error handling, edge cases |
| 9 | `/adapt` | Responsive breakpoints |
| 10 | `/optimize` | Performance |
| 11 | `/animate` | Purposeful motion |
| 12 | `/delight` | Personality and joy |
| 13 | `/bolder` or `/quieter` | Intensity calibration |
| 14 | `/overdrive` | Technically ambitious effects (optional) |
| 15 | `/polish` | Final sweep (always runs) |

**Smart skip:** Before each step, the workflow checks whether `/audit` or `/critique` found issues in that category. No issues found? It skips the step automatically. You can force-run any skipped step by typing the command name.

**Interactive check-ins:** After every step, the workflow pauses. Continue, skip ahead, stop early, or give feedback.

**Before/after comparison:** Baseline audit scores and screenshots are captured at the start. After treatment, a second audit runs and presents a side-by-side delta.

---

### `/improve` -- Targeted Fix Loop

Don't need the full 15-step treatment? `/improve` runs the diagnostic, recommends which commands to apply, and lets you pick.

**Flow:**

```
/audit + /critique
       |
  Synthesize findings
       |
  Map to Impeccable commands
       |
  Present grouped recommendations
       |
  You pick which to run
       |
  Execute selected -> /polish
       |
  Offer re-check
```

This is the workflow you'll use most often. Quick diagnosis, targeted fixes, fast iteration.

---

## The Recommendation Loop

The shared engine powering all three skills.

```
1. /audit         -> technical findings (scores, errors, accessibility)
2. /critique      -> UX assessment (what works, what doesn't, what's mediocre)
3. Synthesize     -> deduplicate, merge overlapping findings
4. Map            -> assign each finding to an Impeccable command
5. Group + Order  -> cluster by command, sort by severity
6. Present        -> numbered list with severity tags
7. User picks     -> run selected commands in sequence
8. /polish        -> final sweep after all fixes
9. Offer re-check -> verify improvements with another audit
```

### Finding-to-Command Mapping

| Finding Category | Command |
|-----------------|---------|
| Over-engineered, unnecessary complexity | `/distill` |
| Layout/spacing issues | `/arrange` |
| Typography issues | `/typeset` |
| Color/contrast issues | `/colorize` |
| Design system inconsistency | `/normalize` |
| Copy/label clarity | `/clarify` |
| Onboarding/empty states | `/onboard` |
| Error handling/edge cases | `/harden` |
| Responsive breakpoints | `/adapt` |
| Performance issues | `/optimize` |
| Motion/animation gaps | `/animate` |
| Missing delight/personality | `/delight` |
| Too bland/safe | `/bolder` |
| Too noisy/aggressive | `/quieter` |
| Technically ambitious effects | `/overdrive` |

---

## Installation

### Claude Code (recommended)

```bash
cp -r dist/claude-code/commands/* ~/.claude/commands/
```

### Cursor

```bash
cp -r dist/cursor/skills/* your-project/.cursor/skills/
```

### Gemini CLI

```bash
cp -r dist/gemini/skills/* your-project/.gemini/skills/
```

---

## Multi-Surface Context

Impeccable reads `.impeccable.md` at the project root for design context (brand colors, typography rules, component patterns). If your project has multiple design surfaces, you need different contexts for each.

**The problem:** Your SaaS has a marketing site, a dashboard, and a docs site. They share a brand but have completely different design rules. Running `/typeset` with the marketing site context on your dashboard will produce wrong recommendations.

**The solution:** Maintain separate `.impeccable.md` files and swap them before running commands.

```
config/impeccable/
  marketing.md      # Bold, editorial, large type
  dashboard.md      # Dense, functional, data-first
  docs.md           # Clean, readable, code-friendly
```

Swap before running any skill:

```bash
cp config/impeccable/dashboard.md .impeccable.md
# Now run /improve, /full-treatment, etc. -- context is dashboard-aware
```

The skills handle this automatically when configured. Add `.impeccable.md` to your `.gitignore` -- it's a transient working file.

---

## Example Contexts

Pre-built `.impeccable.md` templates in `config/examples/`:

| Template | Optimized For |
|----------|---------------|
| `saas-dashboard.md` | Data-dense admin panels, tables, forms |
| `marketing-site.md` | Landing pages, hero sections, CTAs |
| `documentation.md` | Technical docs, code blocks, navigation |
| `ecommerce.md` | Product pages, carts, checkout flows |

Use these as starting points. Run `/teach-impeccable` on your actual pages to generate a tailored context, then merge in what's useful from the templates.

---

## Requirements

- **[Impeccable](https://github.com/pbakaus/impeccable)** installed and configured
- **Playwright MCP server** or **Chrome DevTools MCP server** (for rendering pages during audit/critique)
- **Claude Code**, **Cursor**, or **Gemini CLI**

---

## How It Works

These are skill files -- structured instructions that tell the AI agent to invoke Impeccable commands in a specific sequence with synthesis logic between steps.

There is no runtime, no dependencies, no build step. The skills are plain Markdown files that your AI coding tool reads as instructions. The orchestration logic (smart skip, recommendation mapping, before/after comparison) is encoded directly in the skill text.

The AI does the heavy lifting: rendering pages, running Impeccable commands, synthesizing findings across multiple diagnostic passes, and presenting results in the format specified by each skill.

---

## License

MIT
