## Website Analysis: stripe.com

### What's Costing You Customers

1. **86% of your images are invisible to search engines and screen readers.** 31 out of 36 images on the homepage have no descriptive text. Google cannot index what it cannot read, and the 15-20% of visitors using assistive technology get a blank experience. Every missing image description is a missed chance to rank and a visitor who bounces because the page feels broken.

2. **80% of your clickable elements are too small to tap on a phone.** 146 of 183 buttons and links fail the 44x44px minimum touch target standard. On mobile -- where the majority of web traffic now originates -- visitors misclick, get frustrated, and leave. Each failed tap is a potential signup that walks away.

3. **There is no way for keyboard-only users to skip to content.** 182 focusable elements lack visible focus indicators, and there is no skip-navigation link. Power users, accessibility-dependent visitors, and anyone navigating without a mouse must tab through the entire navigation before reaching any content. Many will give up before they get to "Start now."

### What We'd Improve

1. **Add alt text to all 31 unlabeled images** -- this alone could improve organic search visibility and ensure every visitor understands your value proposition, regardless of how they browse. Expected impact: better image search rankings and compliance with WCAG 2.1 AA.

2. **Increase all touch targets to at least 44x44px** -- particularly the navigation links, footer links, and inline CTAs. This would reduce mobile bounce rates and increase conversion on the "Start now" and "Contact sales" buttons where it matters most.

3. **Add skip-navigation and visible focus indicators** -- a single hidden-until-focused "Skip to main content" link and consistent focus outlines would make the entire site navigable for keyboard users. This is a low-effort change with outsized accessibility impact.

4. **Fix the duplicate H1 heading** -- two identical H1 tags ("Financial infrastructure to grow your revenue") confuse search engine crawlers about the page's primary topic. One clear H1 per page is the standard for SEO.

5. **Reduce the lang attribute precision** -- the page declares `en-MX` (English-Mexico) which may cause search engines and screen readers to apply unexpected regional processing. For a global audience, `en` is more appropriate unless the content is specifically localized for Mexico.

### What Caught Our Eye

1. **The "1.62% of global GDP" live counter is brilliant.** This is not a static stat -- it ticks in real time. It communicates scale and credibility in a way that no case study paragraph ever could. Visitors immediately understand: "This is infrastructure the world depends on."

2. **The case study selection is genuinely impressive.** Hertz, URBN ($5B consolidated), Instacart, Le Monde, Lovable, ElevenLabs ($3B valuation), Supabase (150 countries) -- these are not filler logos. Each one names a specific business outcome with a dollar figure or metric. This is social proof done right.

3. **The visual design is distinctly Stripe, not AI slop.** Custom "sohne-var" typography, the signature purple-indigo palette, the parallelogram motif woven into photography (intersection crosswalks, boutique windows, delivery bags forming the logo shape) -- this is clearly the work of an in-house design team with a strong brand system. No gradient text, no glassmorphism, no generic card grids.

4. **The page structure guides decision-making intelligently.** The flow moves from "what we do" (payments, billing, issuing, crypto) to "who trusts us" (enterprise case studies) to "how to start" (three clear paths: no-code, pre-integrated, or build your own). Each section answers the next logical question a visitor would ask.

### Technical Details (internal)

#### Audit Findings

**Anti-Patterns Verdict: PASS.** This is not AI-generated design. Custom typeface (sohne-var), unique parallelogram photography concept, minimal third-party script bloat (only b.stripecdn.com + stripe.com domains), and a clear brand system throughout.

**Severity Summary:**
- Critical: 1 (images missing alt text -- 31/36)
- High: 3 (touch targets, focus indicators, skip navigation)
- Medium: 3 (duplicate H1, lang attribute, console errors)
- Low: 2 (unloaded SourceCodePro font, hero stat text contrast)

**Detailed Issues:**

| # | Severity | Category | Issue | WCAG |
|---|----------|----------|-------|------|
| 1 | Critical | Accessibility | 31/36 images missing alt text, none marked role="presentation" | 1.1.1 (A) |
| 2 | High | Responsive | 146/183 interactive elements below 44x44px touch target | 2.5.5 (AAA) |
| 3 | High | Accessibility | 182 focusable elements with outline:none, no visible focus indicators | 2.4.7 (AA) |
| 4 | High | Accessibility | No skip-navigation link | 2.4.1 (A) |
| 5 | Medium | SEO | Duplicate H1 tags (2 identical H1 elements) | N/A |
| 6 | Medium | Accessibility | lang="en-MX" may cause regional screen reader behavior | 3.1.1 (A) |
| 7 | Medium | Performance | 3 console errors (Google tracking pixel, LinkedIn pixel failures) | N/A |
| 8 | Low | Performance | SourceCodePro font declared but status "unloaded" (unnecessary network request) | N/A |
| 9 | Low | Accessibility | Stats text rgb(100,116,141) on transparent bg -- contrast borderline at 14px | 1.4.3 (AA) |

**Positive Findings:**
- All 35 non-hero images use `loading="lazy"` -- excellent performance practice
- Proper semantic landmarks (header, main, nav, footer, sections)
- All form inputs have associated labels (0 unlabeled inputs)
- Viewport meta tag properly configured with viewport-fit=cover
- No layout-animating CSS transitions detected (good performance)
- Minimal third-party script footprint (2 external domains only)
- Zero animations on layout properties (width/height/top/left)

#### Critique Findings

**Anti-Patterns Verdict: PASS.** Stripe's homepage is one of the strongest brand-designed pages on the web. Zero AI slop tells.

**Overall Impression:** A masterclass in enterprise SaaS homepage design. The page earns trust through specific numbers (not vague claims), demonstrates breadth through real customer outcomes (not logo walls), and funnels visitors through three clear decision paths. The single biggest opportunity is accessibility -- the design excellence is undermined by mechanical a11y gaps that are straightforward to fix.

**What's Working:**
1. **Information architecture flows like a sales conversation.** Problem > proof > solution > how-to-start. No dead-end sections.
2. **Social proof is specific and verifiable.** "$5 billion consolidated" and "65% decrease in support costs" are claims you can check. This builds trust.
3. **The CTA strategy is well-layered.** "Start now" (self-serve) and "Contact sales" (enterprise) appear at natural decision points, not shoved into every section.

**Priority Design Issues:**
1. **The mobile experience is compromised by touch target sizes.** 80% of interactive elements are too small. This is the gap between "looks beautiful" and "works beautifully."
2. **No visible keyboard navigation path.** A design-conscious site should have design-conscious focus states, not just suppress them.
3. **The footer is a product catalog, not a navigation aid.** 30+ product links in the footer create choice paralysis rather than guiding visitors.

**Questions to Consider:**
- Could the footer be restructured into 4-5 clear categories instead of a flat list of 30+ products?
- What if focus states used Stripe's signature purple instead of being hidden?
- The "Book of the week" section is charming but potentially confusing for first-time visitors looking for payment infrastructure -- is it earning its placement?
