---
name: prospect-audit
description: "Audit any website and generate a business-language analysis with actionable recommendations"
---

# /prospect-audit — Website Analysis for Business Decisions

Read-only analysis. Never edits code or deploys anything.

```
/prospect-audit [url]
```

## Use Cases

- **Sales prospecting** — Specific talking points no generic email could have
- **Self-audit** — See your site through your customers' eyes
- **Client reporting** — "Here's what we found" or "Here's what we fixed"
- **Competitive analysis** — Understand a competitor's strengths and weaknesses

---

## Step 0: Browser Check (first run only)

This skill requires a browser to load and inspect live websites. Check if browser MCP tools are available:

1. **Check for Playwright MCP** — look for tools like `mcp__playwright__browser_navigate`
2. **Check for Chrome DevTools MCP** — look for tools like `mcp__chrome-devtools__navigate_page`

**If neither is available**, stop and guide the user:

```
This skill needs a browser to inspect websites. You need at least one of:

1. **Playwright MCP** (headless, best for automated audits):
   claude mcp add playwright -- npx @playwright/mcp@latest

2. **Chrome DevTools MCP** (controls your real browser, sees what you see):
   Install the superpowers-chrome plugin:
   claude plugin add superpowers-chrome

Recommend installing both — Playwright for fast automated scans,
Chrome DevTools for inspecting what the user actually experiences.

Install one or both, then re-run /prospect-audit.
```

**If at least one is available**, proceed. Prefer Playwright for the initial page load (faster, headless). Use Chrome DevTools when you need to inspect the page as the user sees it (cookie banners, geo-specific content, logged-in states).

---

## Step 1: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first.

## Step 2: Load & Diagnose

1. Navigate to the URL via browser. Wait for full render.
2. **Take a desktop screenshot** (full viewport, above the fold). Save to `clients/<domain>/screenshot-desktop.png`.
3. **Take a mobile screenshot** — resize viewport to 375x812 (iPhone), screenshot above the fold. Save to `clients/<domain>/screenshot-mobile.png`.
4. Run `/audit` — accessibility, performance, theming, responsive, anti-patterns
5. Run `/critique` — visual hierarchy, information architecture, emotional resonance
6. Gather additional signals from the live page:
   - Page title, meta description, OG tags, Schema.org markup
   - Font stack, H1 content, images without alt text
   - Console errors, load timing
   - Mobile touch targets, horizontal overflow

## Step 3: Generate Brief

Synthesize all findings into the brief using the rules below.

---

## Finding-to-Command Mapping

Use this table to categorize audit + critique findings. In prospect-audit, the mapping is used to organize the brief — not to run fixes.

| Finding Category | Maps to | What It Means |
|-----------------|---------|---------------|
| Typography issues (scale, hierarchy, line-height, font pairing) | `/typeset` | Type scale and font relationships need work |
| Color/contrast issues (palette, contrast ratios, color harmony) | `/colorize` | Color system needs rebuilding or adjusting |
| Layout/spacing issues (alignment, grid, whitespace, padding) | `/arrange` | Spatial relationships and layout structure are off |
| Too bland, safe, or generic | `/bolder` | Design needs more confident choices |
| Too noisy, aggressive, or cluttered | `/quieter` | Visual noise needs reducing |
| Motion/animation gaps (no transitions, static interactions) | `/animate` | Purposeful motion is missing |
| Copy/label clarity (confusing labels, vague CTAs, jargon) | `/clarify` | UI text needs rewriting for clarity |
| Over-engineered (too many elements, unnecessary complexity) | `/distill` | Needs stripping to essentials |
| Error handling/edge cases (empty states, loading, failures) | `/harden` | Not resilient to real-world conditions |
| Performance issues (heavy assets, render blocking, layout shifts) | `/optimize` | Performance bottlenecks present |
| Responsive breakpoints (broken on mobile/tablet, missing queries) | `/adapt` | Responsive behavior is broken |
| Missing delight/personality (functional but forgettable) | `/delight` | Needs moments of personality |
| Design system inconsistency (mixed patterns, one-off styles) | `/normalize` | Inconsistent component/token usage |
| Onboarding/empty states (no guidance, blank screens, cold starts) | `/onboard` | First-run experience is missing |
| Technically ambitious effects (3D, shaders, advanced CSS, scroll-driven) | `/overdrive` | Opportunity for standout technical moments |

### Ambiguous Findings

| Finding | Seems like | Actually | Why |
|---------|-----------|----------|-----|
| "Buttons look different on every page" | `/colorize` | `/normalize` | Consistency problem, not color problem |
| "Too much whitespace" | `/arrange` | `/distill` if sparse, `/arrange` if spacing wrong | Check content density vs spacing values |
| "Text is hard to read" | `/typeset` | `/colorize` if contrast, `/typeset` if scale/weight | Check what specifically makes it hard |
| "Page feels slow" | `/optimize` | `/animate` if perceived, `/optimize` if measured | Check actual vs perceived performance |

---

## Brief Template

### Framing Rule

**Write for the business owner, NOT for a developer.**

Every finding must answer: **"What does this cost me in customers or money?"**

| BAD (developer speak) | GOOD (business impact) |
|-----------------------|----------------------|
| "7/8 images missing alt text, fails WCAG AA" | "Google can't read your images — you're invisible for local searches" |
| "10 JavaScript console errors" | "Your animations are broken — visitors see a static page" |
| "No meta description tag" | "When someone Googles you, they see a random snippet instead of your message" |
| "CLS score 0.42" | "Your page jumps around while loading — visitors think it's broken" |

### Vertical-Aware Framing

Detect the business type from the site content, then adjust what you emphasize:

| Business type | What they care about most | Frame findings around |
|---------------|--------------------------|----------------------|
| Local service (restaurant, dentist, salon, trades) | Foot traffic, phone calls, Google Maps | Local search visibility, mobile experience, click-to-call |
| E-commerce / retail | Conversions, cart completion, trust | Page speed, product presentation, checkout friction |
| SaaS / tech | Credibility, sign-ups, demo requests | Professional polish, CTA clarity, load performance |
| Professional services (law, consulting, agency) | Trust, authority, lead quality | Design sophistication, content clarity, social proof |

Don't force-fit — use the business type to prioritize which findings lead, not to invent problems that aren't there.

### Competitive Context

When highlighting a weakness, compare to what visitors expect — not abstract standards:

- BAD: "Your load time is 4.2 seconds"
- GOOD: "Most sites in your space load in under 2 seconds — visitors who wait 4 seconds are already checking your competitor"
- BAD: "No Schema.org markup found"
- GOOD: "Your competitors show star ratings and business hours right in Google results. You show a plain blue link."

You don't need to audit a competitor. Frame against industry norms and visitor expectations.

### Overall Score

After synthesizing all findings, assign a score from 1 to 10:

**"How well does this site convert visitors into customers?"**

| Score | Meaning |
|-------|---------|
| 1-3 | Actively losing business — broken fundamentals |
| 4-5 | Functional but underperforming — obvious gaps |
| 6-7 | Solid foundation — specific improvements would make a real difference |
| 8-9 | Strong — minor polish needed |
| 10 | Exceptional — hard to improve |

Base the score on business impact, not technical perfection. A site with console errors but great conversion flow scores higher than a technically clean site that confuses visitors.

### Effort Labels

Tag each recommendation with an effort estimate:

| Label | Meaning | Examples |
|-------|---------|---------|
| **Quick win** | Under a day, no redesign needed | Add meta description, fix broken link, increase button size |
| **Small project** | A few days of focused work | Rework navigation, improve mobile layout, fix heading hierarchy |
| **Larger project** | A week or more, may need design/strategy | Full responsive overhaul, content restructure, new onboarding flow |

Be honest. Underestimating effort destroys trust when the client finds out later.

### Output Format

```markdown
## Website Analysis: [domain]

**Score: X/10** — [one sentence explaining the score]

![Desktop](clients/<domain>/screenshot-desktop.png)
![Mobile](clients/<domain>/screenshot-mobile.png)

### What's Costing You Customers
- [2-3 problems as LOST BUSINESS or LOST TRUST]
- Lead with the impact, not the technical cause
- Frame against what competitors or visitors expect

### What We'd Fix (in priority order)
1. [Highest impact fix] · _[effort label]_
2. [Second highest] · _[effort label]_
3. [Third] · _[effort label]_
4. [etc.] · _[effort label]_
5. [etc.] · _[effort label]_

### What Caught Our Eye
- [3-4 POSITIVE observations — see specificity rules below]

### Technical Details (internal — do NOT send to client)
- [Raw /audit and /critique findings]
```

Priority order: rank by business impact, not technical severity. A broken contact link outranks a missing alt tag because it directly blocks revenue.

### "What Caught Our Eye" — Specificity Rules

This section builds trust. Generic compliments destroy it. Every positive must:

1. **Name the exact element.** Not "nice design" but "the hero image of your team in the workshop"
2. **Explain WHY it works.** Not "good color choice" but "the teal accent against the dark background makes your CTAs impossible to miss"
3. **Connect to business impact.** Not "clean layout" but "the service cards with prices visible upfront — that saves visitors a phone call and builds trust"

If you can swap in any other business name and the compliment still works, it's too generic. Rewrite it.

### Writing Rules

1. No jargon in client-facing sections (CLS, WCAG, DOM → Technical Details only)
2. Reference their actual business, content, images by name
3. Max 3 items per section (except Technical Details) — prioritize by business impact
4. Positive section is mandatory — never produce an all-negative brief

---

## Save

1. Save brief to `clients/<domain>/analysis_YYYY-MM-DD.md` (or ask where)
2. Display client-facing sections in chat
3. Offer next steps (outreach email, `/improve` to fix)

---

## Localization

The brief MUST match the prospect's language. Detect from `<html lang="">`, visible content, or meta tags. Default to English if unclear.
