## Website Analysis: stripe.com

### What's Costing You Customers

Let's be honest: Stripe's website is exceptionally well-built. This is one of the best homepages on the internet. But even at this level, there are details that leave money on the table:

1. **31 out of 36 images have no text descriptions (alt text).** When Google crawls your site, it can't "see" images -- it reads the descriptions you attach to them. Without those descriptions, you're invisible in Google Image Search and your pages rank lower than they should. For a company spending heavily on content marketing, that's free organic traffic being thrown away.

2. **31 interactive elements on mobile are too small to tap comfortably.** Apple and Google both recommend touch targets of at least 44px. Your client logo carousel links (34px tall) and the "Contact sales" link in the header (20px tall) are undersized. On a phone, a visitor who fumbles a tap on "Contact sales" might just leave instead of trying again. Every missed tap is a missed conversation.

3. **The page serves the Mexico localization (en-mx) instead of detecting visitor location accurately.** A visitor from the US or Europe landing on `/en-mx` sees Mexico-specific pricing and content. That creates a moment of confusion -- and confused visitors don't convert.

### What We'd Fix

1. **Add descriptive alt text to all 31 images.** This would immediately improve search visibility and accessibility compliance. Screen reader users (and there are more than you think) would also be able to understand your product showcase sections.

2. **Increase mobile touch targets to 44px minimum.** The logo carousel links, header navigation, and "Contact sales" CTA all need larger tap areas. This is a CSS-only fix that takes a day and directly increases mobile conversion rates.

3. **Trim the page weight and improve Time to First Byte.** TTFB is 677ms and full load takes 2.4 seconds. For a payments company where trust is everything, shaving that to under 1.5 seconds would measurably reduce bounce rates -- especially on mobile connections in emerging markets.

4. **Fix the duplicate H1 tag.** The page has two identical H1 headings. Search engines expect exactly one H1 per page. This is a quick HTML fix that sharpens your SEO signal.

5. **Implement hreflang tags or smarter geo-routing.** Instead of defaulting everyone to the Mexico locale, serve the right language and region automatically. This prevents the "wrong country" friction that costs enterprise leads.

### What Caught Our Eye

1. **The hero section is outstanding.** "Financial infrastructure to grow your revenue" is one of the clearest value propositions in fintech. The animated gradient background, the real-time GDP counter ("Global GDP running on Stripe: 1.62%"), and the dual CTA ("Get started" + "Sign up with Google") -- this is textbook conversion design. No wasted words, immediate credibility.

2. **Social proof is done perfectly.** The scrolling logo bar (OpenAI, Amazon, Nvidia, Ford, Google, Shopify, Figma, Anthropic, Uber) isn't just name-dropping -- each logo links to a detailed case study. The stats section ("135+ currencies, $1T+ processed, 99.999% uptime, 2000+ enterprise clients") answers every trust objection before it forms.

3. **The product showcase section is best-in-class.** Instead of listing features, Stripe shows interactive product cards (Payments, Billing, Connect, Radar, Atlas) with real UI previews. A visitor can understand what they're buying without reading a single paragraph. The terminal code snippet at the top speaks directly to developers -- Stripe's primary buyer.

4. **Page structure and SEO fundamentals are solid.** Schema.org markup (WebSite + Organization), complete Open Graph and Twitter Card tags, proper canonical URL, viewport meta with `viewport-fit=cover`, 12 preload/prefetch hints, and 35 of 36 images use lazy loading. This is a team that understands performance engineering.

### Technical Details (internal)

| Metric | Value |
|--------|-------|
| **Page Title** | Stripe \| Financial Infrastructure to Grow Your Revenue |
| **Meta Description** | Stripe is a financial services platform that helps all types of businesses accept payments, build flexible billing models, and manage money movement. |
| **Canonical URL** | https://stripe.com/en-mx |
| **HTML Lang** | en-MX |
| **Viewport** | width=device-width, initial-scale=1, viewport-fit=cover |
| **TTFB** | 677ms |
| **DOM Interactive** | 1,054ms |
| **DOM Content Loaded** | 1,599ms |
| **Full Page Load** | 2,433ms |
| **Transfer Size** | 164 KB (initial document) |
| **Font Stack** | sohne-var (custom variable font) |
| **Total Images** | 36 |
| **Images Missing Alt** | 31 (86%) |
| **Lazy-Loaded Images** | 35 |
| **Decorative Images (aria)** | 1 |
| **Total Links** | 172 |
| **External Links** | 29 |
| **H1 Tags** | 2 (duplicate -- same text rendered twice) |
| **H2 Tags** | 5 |
| **Schema.org Types** | WebSite, Organization |
| **OG Tags** | 5 (title, description, image, url, type) |
| **Twitter Cards** | summary_large_image, @stripe |
| **Preconnect Hints** | q.stripe.com, r.stripe.com, images.stripeassets.com, assets.stripeassets.com, b.stripecdn.com |
| **Preload/Prefetch** | 12 resources |
| **Console Errors** | 0 |
| **Console Warnings** | 0 |
| **Horizontal Overflow (375px)** | None detected |
| **Small Touch Targets (<44px)** | 31 elements |
| **Mobile Touch Target Details** | Logo links: 142x34px, Contact sales: 96x20px, Stripe logo: 60x25px, Hamburger menu: 40x40px |

**CTAs identified:** Start now, Get started, Contact sales, Sign in, Sign up with Google, Stripe for startups, Stripe Atlas

---
*Analysis performed 2026-03-22 via automated Playwright audit.*
