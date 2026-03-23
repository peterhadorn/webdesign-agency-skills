## Website Analysis: wellsfargo.com

### What's Costing You Customers

**1. The homepage tries to do everything at once, so visitors do nothing.**
The page presents a login form, a $325 checking bonus, a 60,000-point credit card offer, a $125 student bonus, a savings pitch, interest rate tools, another credit card promo, financial guidance, a chatbot plug, community messaging, AND a help section -- all competing for attention simultaneously. When a new visitor lands here, they have no clear path. Research consistently shows that more choices = fewer conversions. Every section screams "look at me" with equal visual weight, so nothing wins. Prospective customers who came to open an account or explore a product are likely bouncing because the page doesn't guide them anywhere specific.

**2. The sign-on box dominates the page -- pushing new customers aside.**
The very first thing visitors see is a login form with "Good afternoon" and username/password fields. This is great for existing customers, but it tells every new prospect: "This page isn't for you." The $325 checking bonus -- arguably the strongest acquisition hook on the page -- sits below the fold, competing with the sign-on panel. New customer acquisition is being sacrificed to serve existing customers who could just as easily use a dedicated sign-on page or the mobile app.

**3. Promotional overload dilutes every offer.**
There are at least five separate promotional offers visible on the homepage: $325 checking bonus, 60,000 credit card points (appears twice with different cards), $125 student bonus, and a savings account push. When you promote everything, you promote nothing. Each offer cannibalizes attention from the others. A visitor interested in the checking bonus gets distracted by the credit card. A student sees the $325 offer first and may never scroll to find the $125 one meant for them. This is leaving conversions on the table.

### What We'd Improve

1. **Give new visitors a clear entry point.** Separate the experience for existing customers (sign-on) from prospects (product discovery). A simple "New to Wells Fargo?" path with a single, focused call-to-action would dramatically improve conversion for new account openings.

2. **Lead with one hero offer, not five.** Pick the highest-converting promotion and give it the spotlight. Rotate offers by segment or season rather than displaying them all at once. One strong offer converts better than five competing ones.

3. **Create a visual hierarchy that guides the eye.** Right now, every section uses similar-sized headings and similar visual weight. A clear top-to-bottom flow -- hero offer, then supporting products, then trust/community content -- would keep visitors engaged longer and moving toward action.

4. **Simplify the "How can we help?" section.** The bottom of the page has "Find a location," "Make an appointment," and "Quick help" -- useful actions buried where few visitors scroll. These utility actions should be more accessible, possibly in the header or as a persistent element.

5. **Reduce the footer legal density.** The footer contains extensive legal disclaimers, trademark notices, and compliance text that, while necessary, creates an intimidating wall of fine print. Better formatting (collapsible sections, lighter typography) would maintain compliance without overwhelming visitors.

### What Caught Our Eye

1. **Strong semantic HTML and accessibility foundations.** The page uses proper heading hierarchy (h1 through h3), landmark regions (banner, main, navigation, contentinfo), descriptive link text, and labeled form inputs. This is enterprise-grade accessibility work that many competitors skip entirely. Screen reader users and keyboard navigators are well-served.

2. **Clear, benefit-driven copywriting on individual offers.** Headlines like "$325 checking bonus on us" and "New customer? Say hello to a $125 bonus" are direct, specific, and action-oriented. The copy doesn't waste words and each offer section has a clear CTA. The writing quality is strong -- the problem is volume, not craft.

3. **Thoughtful security and trust signals.** The "Your shield against scams" section, prominent privacy/security links, passkey sign-on option, and FDIC/SIPC disclosures build institutional trust. For a financial services site, this is essential and well-executed. The inclusion of fraud reporting in the footer shows customer-first thinking.

4. **Bilingual support (Español link in header).** Having Spanish-language access prominently in the top navigation demonstrates inclusivity and expands the addressable market. Many competitors bury language options or omit them entirely.

### Technical Details (internal)

#### Audit Findings

**Anti-Patterns Verdict: PASS** -- This is clearly a professionally designed enterprise site, not AI-generated. No gradient text, no glassmorphism, no glowing dark-mode accents, no generic card grids. The design is corporate and conservative, which is appropriate for a financial institution.

**Accessibility (largely strong):**
- PASS: Proper heading hierarchy (h1 > h2 > h3), landmark regions, labeled form inputs
- PASS: Skip-to-content link present
- PASS: Descriptive link text on most CTAs (e.g., "Get Started and find out how to get a $325 checking bonus")
- MEDIUM: Social media links in footer use `href="#"` -- these are non-functional placeholder links that would confuse screen reader users and keyboard navigators
- MEDIUM: Some decorative characters (`\u200d` zero-width joiners) used as spacers in headings -- screen readers may announce these oddly
- LOW: Password field has "Show password" toggle -- good pattern, implementation should be verified for screen reader announcement

**Performance:**
- 8 console errors related to Content-Security-Policy directives -- these are configuration issues, not user-facing, but indicate CSP headers need cleanup
- Multiple external redirects in CTAs (accountoffers.wellsfargo.com, creditcards.wellsfargo.com, connect.secure.wellsfargo.com) add latency to conversion paths
- Interest rate "Check rates" button is a dropdown that requires JS -- if JS fails, this core feature breaks

**Information Architecture:**
- CRITICAL: No clear visual hierarchy -- 5+ promotional sections with equal visual weight
- HIGH: Sign-on form dominates above-the-fold space, deprioritizing acquisition
- MEDIUM: "Ask Fargo" AI assistant section feels disconnected from the page flow
- MEDIUM: "Serving our customers and communities" section is brand messaging that interrupts the product flow

**Navigation:**
- PASS: Clear top-level segmentation (Personal, Investing, Business, Commercial, Corporate, About)
- PASS: Sub-navigation under Personal is well-organized (Checking, Savings, Credit Cards, etc.)
- MEDIUM: Main nav items link to top-level pages but sub-items only appear on hover/interaction -- mobile behavior should be verified

**Responsive Design:**
- Could not fully assess without viewport resizing, but the structure suggests proper responsive implementation given the enterprise nature of the build
- The multi-column promotional grid (3 cards: credit card, student bonus, savings) would need careful stacking on mobile

**Content Strategy:**
- The page serves two audiences (existing customers, prospects) without clearly separating them
- Promotional offers appear in at least 3 different visual formats (hero banner, card grid, secondary banner), creating inconsistency
- The "Autograph Journey" credit card appears in two separate sections -- redundant

#### Critique Findings

**Overall Impression:** A technically competent but strategically unfocused homepage. It reads like a committee designed it -- every department got their section, and nobody prioritized. The individual pieces are well-crafted, but the whole is less than the sum of its parts.

**Visual Hierarchy:** Weak. The sign-on form, hero banner, card grid, and secondary promotions all compete at similar visual weights. There is no clear "most important thing" on the page. A new visitor's eye has no guided path.

**Emotional Resonance:** The page evokes "corporate reliability" -- which is on-brand for a major bank. However, it lacks warmth. The "Good afternoon" greeting is a nice touch, but it's attached to a login form, not a welcoming experience. The community section tries to add warmth but feels obligatory.

**Typography:** Conservative and readable. Heading hierarchy is clear in the HTML but visually, multiple h2-level headings at similar sizes flatten the hierarchy. Body text is appropriately sized.

**Color:** The Wells Fargo red/yellow brand palette is used consistently. Color is functional (red for primary brand, standard link colors) rather than decorative. No accessibility issues with the palette itself, though specific contrast ratios would need measurement against backgrounds.

**Composition:** The page is long and sectioned, with clear visual breaks between areas. However, the sections feel like stacked modules rather than a flowing narrative. The rhythm is: promo, promo, promo, guidance, app plug, community, help -- there's no storytelling arc.

**Key Questions:**
- What if the homepage had two distinct entry points: "I'm a customer" (sign on) vs. "I'm exploring" (product discovery)?
- What if there was ONE hero offer instead of five, with the others accessible via tabs or a secondary page?
- Does the "Serving our communities" section belong on the homepage, or would it have more impact on an About page where visitors are already in learning mode?
