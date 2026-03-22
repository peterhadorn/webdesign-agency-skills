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

## Step 1: Load

- **URL** — Navigate via Playwright to render the page
- **Local file** — Read the file into context
- If load fails: report error and abort

## Step 2: Context

Check `.impeccable.md` at project root. If missing, run `/teach-impeccable` first or copy from `config/examples/`.

## Step 3: Diagnose

Run on the loaded page:

1. `/audit` — accessibility, performance, theming, responsive, anti-patterns
2. `/critique` — visual hierarchy, information architecture, emotional resonance

## Step 4: Generate Brief

Synthesize audit + critique findings into the brief below.

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

### Output Format

```markdown
## Website Analysis: [domain]

### What's Costing You Customers
- [2-3 problems as LOST BUSINESS or LOST TRUST]
- Lead with the impact, not the technical cause

### What We'd Improve
- [3-5 improvements as OUTCOMES]
- "Make Google show your business properly" not "Add meta description"

### What Caught Our Eye
- [3-4 POSITIVE observations referencing specific content by name]
- Always include at least one genuine compliment

### Technical Details (internal — do NOT send to client)
- [Raw /audit and /critique findings]
```

### Rules

1. No jargon in client-facing sections (CLS, WCAG, DOM → Technical Details only)
2. Reference their actual business, content, images by name
3. Max 3 items per section (except Technical Details)
4. Positive section is mandatory

---

## Step 5: Save

1. Save brief to `clients/<domain>/analysis_YYYY-MM-DD.md` (or ask where)
2. Display client-facing sections in chat
3. Offer next steps (outreach email, `/improve` to fix, `/compare` vs competitor)

---

## Optional Extensions

Not part of the core workflow. Use when deeper data is needed on top of audit + critique.

- **SEO deep dive** — Title quality, heading hierarchy, canonical URLs, robots.txt, sitemap, OG tags, Schema.org
- **Performance analysis** — Core Web Vitals, resource count, transfer size, render-blocking resources
- **Technical extraction** — Console errors, load timing, touch target sizes, font stack, images without alt (counted via JS)
- **Sales brief formatting** — Localize to site language, draft outreach email from findings
