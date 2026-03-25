## Website Analysis: webevolve.ch

> Self-audit produced by `/prospect-audit` — testing the tool on our own site.

**Score: 5/10** — Strong headline and pricing transparency, but broken contact links and slow load time are actively losing leads.

### What's Costing You Customers

- **Three contact links don't work.** "E-Mail schreiben", "Auf WhatsApp schreiben", and "Cookie-Einstellungen" all lead nowhere. A prospect who wants to reach you clicks, nothing happens, and they leave. That's a lost lead.
- **The site takes over 4 seconds to fully load.** For a business that criticizes slow websites ("Überladen und langsam"), this is a contradiction visitors will notice — consciously or not.
- **The body text uses the most generic font on the internet.** Inter is the default choice of every AI-generated landing page. For a company selling design quality, the font choice undermines the message.

### What We'd Fix (in priority order)

1. **Fix the dead contact links** — wire up the actual mailto:, WhatsApp deeplink, and cookie consent handler. These are direct conversion paths that currently go nowhere. · _Quick win_
2. **Cut the load time below 2 seconds** — audit the 6 scripts, defer non-critical JS, check hosting. A site selling speed should be fast. · _Small project_
3. **Replace Inter with a distinctive body font** — Source Sans 3, General Sans, or Bricolage Grotesque would match the bold tone of the hero without screaming "template." · _Quick win_
4. **Remove emoji from B2B headings** — "Verpasste Aufträge" is already clear without 💸. The emojis make the page feel casual in a context where authority matters. · _Quick win_
5. **Add basic accessibility landmarks** — a `<main>` wrapper and skip-navigation link. Quick wins that signal professionalism. · _Quick win_

### What Caught Our Eye

- **"Ist Ihre Website PEINLICH?" is a killer headline.** Bold, confrontational, impossible to ignore. Most Swiss agencies play it safe — this stands out immediately.
- **Transparent pricing on the homepage (ab CHF 390)** — no "Preis auf Anfrage", no hidden costs. This builds instant trust with KMU owners who've been burned by agencies before.
- **The "Gratis-Entwurf" offer eliminates risk.** Free draft in one business day, no commitment — there's almost no reason NOT to try. Smart conversion strategy.
- **Real company address in Appenzell with proper Impressum** — feels local and legitimate, not a faceless template operation.

### Technical Details (internal)

**Audit findings:**
- Lang: `de` — correct
- Title: "Website Redesign Schweiz | Festpreis & Gratis-Entwurf | WebEvolve" — keyword-first, good
- Meta description: present, under 160 chars, includes pricing and USP
- OG tags: present (title, image)
- Schema.org: 1 JSON-LD block
- H1: 1x "Website Redesign für Schweizer KMU" — correct single H1
- Heading hierarchy: H1 → H2 → H3 — clean, no skips
- Images: 3 total, 0 missing alt — perfect
- Fonts: Inter (body), Outfit (headings)
- TTFB: 1,341ms | DOM loaded: 4,233ms | Full load: 4,445ms
- Scripts: 6 external | Stylesheets: 2
- No skip-navigation link
- No `<main>` landmark (1 `<nav>`, 1 `<footer>`)
- 3x `href="#"` dead links (E-Mail, WhatsApp, Cookie-Einstellungen)
- Duplicate comparison table ("Traditionelle Agentur vs. WebEvolve") appears twice
- Missing space in heading: "20 Jahre Erfahrung.Modernste Werkzeuge."

**Critique findings:**
- Anti-patterns: MIXED — Inter font and emoji headings are AI slop tells, but hero design and copy are distinctive
- Visual hierarchy: Strong above the fold, weakens in middle sections
- The 4-card problem grid (💸📱🐌😓) follows a common AI layout pattern
- Outfit for headings is a good distinctive choice
- Red/purple palette is bold and cohesive
- CTA placement is effective (hero + footer)
- Copy is specific Swiss German, not template filler

**Note:** Full-page screenshot shows blank gaps between sections — this is a false positive caused by scroll-reveal animations not triggering in the screenshot. The actual browsing experience shows content correctly.
