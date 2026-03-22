---
name: prospect-audit
description: "Audit any website and generate a business-language sales brief with specific findings and talking points"
---

# /prospect-audit -- Sales Intelligence from Any URL

**Scope:** This skill is READ-ONLY. It never edits code, modifies files on the target site, or deploys anything. It produces a single analysis document.

**Usage:** `/prospect-audit [url]`

---

## Phase 0: Guard

1. Confirm the URL is provided. If missing, ask for it.
2. Load the URL via Playwright (`browser_navigate`).
3. If the page fails to load (404, timeout, SSL error, WAF block, connection refused): report the specific error and **abort**. Do not guess or proceed with partial data.

---

## Context Swap: Impeccable Design Context

Before running `/audit` or `/critique`, check if `.impeccable.md` exists at the project root.

- **If it exists:** Impeccable will use it automatically. No action needed.
- **If it does NOT exist:** Copy from `config/examples/marketing-site.md` or run `/teach-impeccable` to generate one. This file provides the design context Impeccable needs to produce meaningful critiques.

---

## Phase 1: Load

1. Navigate to the URL and wait for the page to fully render (network idle or 5s timeout).
2. Take a full-page screenshot for reference.
3. Note any redirect chains (e.g., `http -> https`, `www -> non-www`).

---

## Phase 2: Diagnose

### Run Impeccable commands

1. Run `/audit` -- captures layout, accessibility, performance, and standards compliance.
2. Run `/critique` -- captures design quality, visual hierarchy, and UX issues.

### Gather additional signals via Playwright

Collect the following from the live page:

| Signal | How |
|--------|-----|
| Page title | `document.title` |
| Meta description | `<meta name="description">` |
| Open Graph tags | `og:title`, `og:description`, `og:image` |
| Schema.org markup | Any `<script type="application/ld+json">` |
| Font stack | Computed font-family on `body` and `h1` |
| H1 content | First `<h1>` text |
| Images without alt | Count of `<img>` elements with empty or missing `alt` |
| Console errors | Any JS errors logged during page load |
| Load time | Navigation timing (domContentLoaded, load event) |
| Mobile touch targets | Buttons/links smaller than 44x44px |
| Horizontal overflow | Whether `document.body.scrollWidth > window.innerWidth` |

---

## Phase 3: Generate the Sales Intelligence Brief

### CRITICAL FRAMING RULE

**Write for the business owner, NOT for a developer.**

The owner of a restaurant, dental practice, or hair salon does not care about
jQuery conflicts, WCAG AA, or touch target pixel sizes. They care about:
losing customers, looking unprofessional, being invisible on Google,
and competitors beating them.

Every finding must answer: **"What does this cost me in customers or money?"**

| BAD (developer speak) | GOOD (business impact) |
|-----------------------|----------------------|
| "7 of 8 images missing alt text, fails WCAG AA accessibility standards" | "Google can't read your images -- you're invisible for local searches like 'dentist near me'" |
| "10 JavaScript console errors ($ is not a function)" | "Your scroll animations are broken -- visitors see a static page instead of the polished experience you paid for" |
| "No meta description tag found" | "When someone Googles you, Google writes its own summary instead of showing YOUR message" |
| "CLS score 0.42, above 0.1 threshold" | "Your page jumps around while loading -- visitors think something is broken and leave" |

### Brief Template

Generate the brief using this structure. The language MUST match the prospect's locale (see Localization below).

```markdown
## Website Analysis: [domain]

### What's Costing You Customers
- [2-3 problems framed as LOST BUSINESS or LOST TRUST]
- Always explain the CONSEQUENCE, not the technical cause
- Lead with the impact: "You're losing X because Y" not "Y is misconfigured"

### What We'd Improve
- [3-5 specific improvements, framed as OUTCOMES not tasks]
- Lead with the RESULT: "Make Google show your business properly" not "Add meta description"
- Be specific: reference actual content, pages, or elements from the site

### What Caught Our Eye
- [3-4 POSITIVE observations that prove we actually looked at their site]
- Reference specific content, design choices, or elements BY NAME
- Always include at least one genuine compliment about their business or brand
- This section builds trust -- it shows this isn't a generic template

### Technical Details (internal -- do NOT send to client)
- [Raw /audit and /critique findings for your reference]
- Scores, metrics, specific errors, element selectors
- This section is for your team only -- never include it in outreach
```

### Writing Rules

1. **No jargon in client-facing sections.** Terms like "CLS", "LCP", "WCAG", "viewport", "DOM" belong only in the Technical Details section.
2. **Be specific, not generic.** Reference their actual business name, services, images, and content. A brief that could apply to any website is worthless.
3. **Max 3 items per section** (except Technical Details). Prioritize by business impact.
4. **Positive section is mandatory.** Never produce an all-negative brief. If the site is genuinely well-made, say so and focus the improvements on smaller optimizations.

---

## Phase 4: Save and Next Steps

1. Save the brief to a file. Suggested path: `clients/<domain>/analysis_YYYY-MM-DD.md`
   - If the `clients/` directory does not exist, ask the user where to save.
2. Display the client-facing sections (everything except Technical Details) in the chat.
3. Offer: **"Want me to draft an outreach email using these findings?"**

---

## Localization

The brief MUST match the prospect's language and locale:

- If the site is in German, write the brief in German.
- If the site is in French, write in French.
- If the site is in Spanish, write in Spanish.
- Default to English if the language is unclear or mixed.

Detect language from: `<html lang="">`, visible page content, or meta tags. When in doubt, ask the user.
