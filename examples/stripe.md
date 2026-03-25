## Website Analysis: stripe.com

**Score: 7/10** — Strong brand and conversion flow, but accessibility gaps and mobile tap targets are leaving money on the table.

### What's Costing You Customers

- **86% of your images are invisible to search engines and screen readers.** 31 out of 36 images on your homepage have no description. Google cannot index what it cannot read, and the 15-20% of visitors using assistive technology (screen readers, slow connections showing alt text) get a broken experience. Every invisible image is a missed chance to rank and convert.

- **73% of your clickable elements are too small for mobile users.** 146 out of 201 buttons and links fail the minimum touch target size. On phones -- where the majority of web traffic happens -- visitors are mis-tapping, getting frustrated, and leaving before they reach your "Get started" button. That is real revenue walking away.

- **There is no way to skip your navigation with a keyboard.** Visitors using keyboards (accessibility needs, power users, anyone with a broken trackpad) must tab through every single navigation item before reaching your content. Many will give up. This also fails a basic web accessibility compliance requirement (WCAG 2.4.1), which carries legal exposure in the US and EU.

### What We'd Fix (in priority order)

1. **Increase touch target sizes on mobile** — buttons and links need to be at least 44x44 pixels. This is a one-time CSS change that immediately reduces mobile bounce rates. · _Quick win_

2. **Add descriptions to every image** — especially the product screenshots and customer logos. This directly improves search engine visibility and makes the site usable for all visitors. · _Quick win_

3. **Add keyboard skip navigation** — a single hidden link that lets keyboard users jump past the menu. Standard practice for any site that cares about accessibility compliance. · _Quick win_

4. **Fix the duplicate page title (H1)** — the main heading is rendered twice in the code. Search engines get confused when a page has two identical titles. · _Quick win_

5. **Reduce decision fatigue in the hero** — "Get started" and "Sign up with Google" and "Contact sales" all compete for attention above the fold. Testing a single primary CTA could lift conversion rates. · _Small project_

### What Caught Our Eye

- **The social proof is outstanding.** OpenAI, Amazon, Nvidia, Google, Shopify, Uber, Anthropic -- this is arguably the strongest customer logo bar on the internet. The scrolling carousel format keeps it dynamic without feeling like a static wall. It immediately communicates credibility at the highest level.

- **The "1.62% of Global GDP" stat is a power move.** Leading with a single metric that quantifies scale is more persuasive than any paragraph of copy could be. It answers "why should I trust you?" before the visitor even asks.

- **Mobile adaptation is genuinely good.** The layout reflows cleanly at 375px -- stacked CTAs, clean hamburger menu, readable typography. The hero gradient and headline maintain their impact on small screens. Most enterprise sites butcher their mobile experience; this one holds up.

- **The customer stories are specific and credible.** "Hertz: 160 countries, 11K+ locations" and "URBN: $5 billion in revenue onto Stripe" -- these are not vague testimonials. They name real companies with real numbers, organized by segment (enterprise, startup, platform). This builds trust because it shows results, not promises.

### Technical Details (internal)

**Audit Metrics (automated scan):**

| Check | Result | Severity |
|-------|--------|----------|
| Skip links | 0 found | Critical (WCAG 2.4.1) |
| Images without alt text | 31/36 (86%) | Critical (WCAG 1.1.1) |
| Empty links (no text or aria-label) | 28/172 | High |
| Duplicate H1 elements | 2 (identical content) | Medium |
| Touch targets < 44px | 146/201 (73%) | High |
| Lazy-loaded images | 35/36 | Good |
| Landmark elements | main, nav, footer present | Good |
| Viewport meta | Properly configured with viewport-fit=cover | Good |
| HTML lang | en-MX (geo-redirected) | Low |
| TTFB | 750ms | Medium |
| DOM Content Loaded | 1038ms | Medium |
| Full page load | 1424ms | Acceptable |
| Total headings | 48 (hierarchy generally sound) | Good |
| Form inputs | 0 (no forms on homepage) | N/A |

**Anti-Patterns Verdict: PASS.** This does not look AI-generated. The gradient color treatment is distinctive and branded (not the generic cyan-on-dark AI palette). Typography choices feel intentional. The layout breaks from rigid card grids with varied section compositions. The "Book of the week" section is genuinely unusual -- no AI would add that to a payments homepage.

**Critique Notes:**

- Hero heading is technically too long -- the subheading ("Accept payments, offer financial services...") is crammed inside the H1 tag rather than being a separate paragraph. Screen readers announce the entire block as a single heading.
- Customer logo carousel duplicates all entries (OpenAI, Amazon, Nvidia, Ford etc. appear twice in the DOM) -- standard infinite scroll technique, but the empty alt text means screen readers encounter unlabeled images.
- The "Flexible solutions" section uses interactive buttons styled as tabs, but their affordance as clickable tabs is weak -- they look like static headings until hovered.
- Page length is extreme (48 headings across enterprise/startup/platform sections). A visitor scanning quickly may never reach the platform or developer sections.
- The "Book of the week" / Stripe Press section is charming but off-brand for a visitor evaluating payment infrastructure. It signals culture, not product value.
- "Join us at Sessions" event promo (April 29-30, 2026, Moscone West) is time-sensitive content that will need removal/update post-event.
- Performance is acceptable but TTFB of 750ms is high for a globally CDN-served page; likely due to geo-detection and redirect logic (stripe.com -> stripe.com/en-mx).
