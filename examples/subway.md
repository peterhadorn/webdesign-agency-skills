## Website Analysis: subway.com

**Audited:** March 22, 2026
**URL:** https://www.subway.com/en-us

---

### What's Costing You Customers

**Your homepage tells Google "Unable to load the page."** The only H1 heading on your site -- the single most important element for search rankings -- reads "Unable to load the page." This is a hidden error message that Google reads as your main headline. When someone searches "Subway near me" or "sandwich delivery," Google sees a broken page title instead of your brand message. This directly hurts your search visibility against competitors like Jimmy John's and Jersey Mike's who have clean, optimized headings.

**Nearly half your images are invisible to search engines and screen readers.** 26 out of 58 images on your homepage have no text description (alt text). That means Google Image Search can't index your food photography, and the 1 in 4 Americans who use screen readers can't understand what's on the page. Every missing alt tag on a product image is a missed chance to appear in "best sandwich" image searches -- traffic your competitors are picking up.

**Broken assets and server errors are slowing your ordering flow.** Five image files in your online ordering interface are returning 500 errors (server failures) -- including the close button, share icon, and pickup icon. When a customer tries to place an order and the interface feels broken or unresponsive, they leave. For a business that processes millions of online orders, even a 1% drop-off from broken UI elements represents significant lost revenue.

---

### What We'd Fix

**Replace the hidden error H1 with a clear, searchable headline.** Something like "Fresh Subs, Salads & More -- Order Online or Find a Subway Near You." This one change would immediately improve how Google understands and ranks your homepage, potentially driving thousands of additional organic visits per month.

**Add descriptive alt text to all 26 images missing it.** Prioritize the menu item photos and promotional images. Each one becomes a new entry point from Google Image Search. A description like "Subway Italian B.M.T. footlong sub with pepperoni, salami, and ham" does the work a salesperson would do in-store.

**Fix the 5 broken server assets in the ordering flow.** The close button, share icon, and pickup icons are all returning 500 errors. These are core interaction elements -- fixing them removes friction from the exact moment a customer is ready to spend money.

**Add structured data (schema.org markup) for Restaurant and Menu.** Your site currently has zero structured data. Adding Restaurant schema would enable rich results in Google -- showing your menu, hours, pricing, and ratings directly in search results. Competitors using this get significantly higher click-through rates.

**Set up Open Graph and Twitter Card meta tags.** When someone shares your site on Facebook, LinkedIn, iMessage, or X (Twitter), there's no preview image, no description, no branded card. It shows up as a plain text link. Every share is a free ad -- right now those ads are blank.

---

### What Caught Our Eye

**Fast page load times.** Your homepage loads in about 1 second with a time-to-first-byte of 474ms. That's solid performance for a content-heavy site with promotions, menus, and ordering functionality. Fast sites keep customers engaged and Google rewards speed in rankings.

**Strong promotional content structure.** The deals section is well-organized with clear pricing ($4.99 Sub of the Day, $6.99 ANY Footlong, $3.99 Protein Pockets) and compelling calls to action. The hierarchy of deals, menu items, and catering gives visitors multiple reasons to convert.

**Clean mobile layout with no horizontal overflow.** At 375px (iPhone width), the site fits perfectly with no sideways scrolling. The responsive design adapts cleanly, which means you're not losing the 60%+ of visitors who come from phones.

**Well-structured footer navigation.** The footer covers all key areas -- nutrition, sustainability, careers, franchising, and social media. It's organized in a way that helps both customers and search engines find important pages deeper in the site.

---

### Technical Details (internal)

**Page Basics**
- Title: `Home | Subway`
- Meta description: "Discover better-for-you sub sandwiches at Subway. View our menu of sandwiches, order online, find restaurants, order catering or buy gift cards."
- Canonical: `https://www.subway.com/en-us`
- HTML lang: `en-US`
- Viewport meta: `width=device-width, initial-scale=1`

**SEO & Social**
- H1 tags: 1 ("Unable to load the page" -- error message rendered as H1)
- H2 tags: 18 (includes duplicates and empty strings)
- H3 tags: 10
- Open Graph tags: 0 (none)
- Twitter Card tags: 0 (none)
- Schema.org (JSON-LD): 0 (none)

**Images**
- Total images: 58
- Missing alt text: 26 (44.8%)
- Broken images (500 errors): 5 (close@2x.png, close@3x.png, close.png, share.png, 05-ui-icon-pickup@3x.png)

**Performance**
- TTFB: 474ms
- DOM Interactive: 602ms
- DOM Content Loaded: 829ms
- Load Complete: 1,003ms
- Initial transfer: 22 KB

**Resources**
- External scripts: 26
- Stylesheets: 7

**Fonts**
- Subway Sans LCG Web (Regular, Bold, Medium)
- Subway Sans Cond Web (Medium, Bold)
- Subway-ROIcons (icon font)
- Fallbacks: Georgia, Helvetica Neue, Helvetica, Arial, sans-serif

**Mobile (375px viewport)**
- Horizontal overflow: None
- Total clickable elements: 222
- Touch targets under 44px: 59 (26.6%)
- Notable undersized targets: hamburger menu (24x26px), navigation buttons (24x24px), carousel controls (30x22px), Terms & Conditions links (110x16px)

**Console Errors (Subway-specific)**
- 10 errors total from subway.com domain
- 5x HTTP 500 on `/Assets/RemoteOrder/img/` resources
- 2x JavaScript parse errors ("Unexpected end of input")
- 1x TypeError in Adobe Launch tag manager (launch-c29f9a12ff43.min.js)
- LaunchDarkly feature flag stream connection errors

**Geo-Routing**
- subway.com (bare domain) redirects based on visitor location -- test showed Mexico locale (es-mx). The en-us path loads the US site correctly. No hreflang tags detected for international SEO signals.
