---
name: prospect-audit
description: "Audit any website and generate a business-language analysis with actionable recommendations"
---

# /prospect-audit — Website Analysis for Business Decisions

Read-only analysis. Never edits code or deploys anything.

```
/prospect-audit [url-or-file]
```

## Use Cases

- **Sales prospecting** — Specific talking points no generic email could have
- **Self-audit** — See your site through your customers' eyes
- **Client reporting** — "Here's what we found" or "Here's what we fixed"
- **Competitive analysis** — Understand a competitor's strengths and weaknesses

---

## Core (Impeccable)

### Step 1: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first or copy from `config/examples/`.

### Step 2: Diagnose

Run on the target page or file:

1. `/audit` — accessibility, performance, theming, responsive, anti-patterns
2. `/critique` — visual hierarchy, information architecture, emotional resonance

### Step 3: Generate Brief

Synthesize audit + critique findings into the brief using the rules below.

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

### Output Format

```markdown
## Website Analysis: [domain]

### What's Costing You Customers
- [2-3 problems as LOST BUSINESS or LOST TRUST]
- Lead with the impact, not the technical cause
- Frame against what competitors or visitors expect

### What We'd Improve
- [3-5 improvements as OUTCOMES]
- "Make Google show your business properly" not "Add meta description"

### What Caught Our Eye
- [3-4 POSITIVE observations — see specificity rules below]

### Technical Details (internal — do NOT send to client)
- [Raw /audit and /critique findings]
```

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

## Extras (conditional)

Run these only when the diagnosis reveals a clear need:

| Trigger | Extra |
|---------|-------|
| >3 console errors or broken interactions detected | Extract: console errors, load timing, font stack via Playwright |
| No meta description, no OG tags, or no Schema.org | SEO check: title quality, heading hierarchy, canonical URLs, robots.txt, sitemap |
| Load time >3s or large unoptimized images found | Performance check: Core Web Vitals, resource count, render-blocking resources |

If no triggers fire, skip extras entirely.

---

## Save

1. Save brief to `clients/<domain>/analysis_YYYY-MM-DD.md` (or ask where)
2. Display client-facing sections in chat
3. Offer next steps (outreach email, `/improve` to fix)

---

## Localization

The brief MUST match the prospect's language. Detect from `<html lang="">`, visible content, or meta tags. Default to English if unclear.
