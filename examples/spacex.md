## Website Analysis: spacex.com

**Audited:** 2026-03-22 | **URL:** https://www.spacex.com/

---

### What's Costing You Customers

**1. Google can't read your website.**
The entire homepage is built with JavaScript -- when Google's crawler visits, it sees an empty page with no text, no headings, no product descriptions. This means Google has to work harder (and sometimes fails) to index your content. For any business relying on organic search traffic, this is like having a beautiful storefront with the shutters down. Potential customers searching for "commercial space launches" or "satellite internet" may never find you through Google.

**2. When people share your link, it looks blank.**
There is no meta description, no Open Graph image, and no social card tags. When someone shares spacex.com on LinkedIn, X, or in a message, the preview shows just the word "SpaceX" with no image and no description. Every share is a missed opportunity to grab attention -- competitors with proper social previews get 2-3x more clicks from shared links.

**3. No H1 heading -- Google doesn't know what your page is about.**
The homepage has zero H1 tags. H1 is the single most important on-page SEO signal telling Google "this page is about X." Without one, you're giving up the clearest signal to search engines about what you do. Every H2 section ("Making life multiplanetary," "Revolutionizing space technology") is well-written, but Google weighs H1 more heavily than H2.

---

### What We'd Fix

**1. Add server-side rendering so Google and social platforms can read the page.**
Right now the HTML that arrives from the server is empty CSS and JavaScript -- all content loads after the browser runs the scripts. By rendering the page on the server first, Google indexes instantly, social previews work automatically, and the page feels faster for visitors on slow connections. This single change unlocks every other SEO improvement.

**2. Add meta description, OG tags, and structured data.**
A clear meta description ("SpaceX designs, manufactures, and launches advanced rockets and spacecraft") directly controls how you appear in Google results. OG tags control how you look when shared on social. Schema.org structured data (Organization type) earns rich results in Google -- logo, social profiles, and company info displayed right in search.

**3. Add a single, clear H1 heading.**
Something like "SpaceX -- Making Life Multiplanetary" as an H1 gives Google an immediate, authoritative signal. The current H2 headings are strong and should remain, but one H1 ties the page together for search engines.

**4. Add alt text to all images.**
At least 10 images on the homepage (logo, navigation icons, section hero images, CTA arrows) have no alt text. Screen readers announce these as "image" with no context, which means visually impaired visitors cannot understand your page. Alt text also gives Google additional keywords to index your images.

**5. Set the HTML lang attribute.**
The page does not declare a language (`lang="en"`). This tells browsers and assistive technology what language to use for pronunciation and translation. A one-line fix that improves accessibility for every visitor.

---

### What Caught Our Eye

**1. Stunning visual storytelling.**
The full-screen hero sections with high-quality photography (Mars, Starship launch, Falcon landing, astronauts, Starlink hardware) create an immersive, cinematic experience. Each section pairs a bold headline with a concise paragraph and a clear call-to-action. This is world-class brand presentation.

**2. Clear, focused content hierarchy.**
Five sections, five messages, five CTAs. The page avoids the common trap of cramming everything onto the homepage. Each section answers one question: Why does SpaceX exist? What are they building? How to book a launch? How to join a mission? How to get Starlink? This clarity respects the visitor's time.

**3. Consistent, confident navigation.**
The hamburger menu is minimal, the footer has exactly four links (Careers, Updates, Privacy Policy, Suppliers), and the X/Twitter link is prominent. No clutter, no dropdown maze. The navigation says "we know what we are and we don't need to over-explain."

**4. Strong CTA language.**
"Explore," "Learn More," "Reserve Your Ride," "Join a Mission," "Order Now" -- each call-to-action uses active, specific verbs that match the section's intent. "Reserve Your Ride" for the rideshare program is particularly effective -- it makes commercial space launches feel accessible.

---

### Technical Details (internal)

| Metric | Value |
|--------|-------|
| **Page title** | "SpaceX" (too short, no keywords) |
| **Meta description** | Missing |
| **OG tags** | None |
| **Twitter/X cards** | None |
| **Schema.org** | None |
| **Canonical URL** | Not set |
| **HTML lang** | Not set |
| **Viewport meta** | Present (responsive) |
| **H1 tags** | 0 |
| **H2 tags** | 5 ("Making life multiplanetary," "Revolutionizing space technology," "World's leading launch service provider," "Advancing human spaceflight," "Delivering high-speed internet from space") |
| **Total images** | ~10 (logo, nav icons, 5 section backgrounds, CTA arrows) |
| **Images missing alt** | ~10 (all images lack alt text) |
| **Console errors** | 1 error on load (LinkedIn pixel blocked by ad script) |
| **Rendering** | Client-side only (SPA) -- server returns empty HTML with CSS/JS |
| **Fonts** | Custom brand font (loaded via @font-face) |
| **Internal links** | 9 (/, /humanspaceflight/mars, /vehicles/starship, /rideshare, /humanspaceflight, /careers, /updates, /supplier, privacy PDF) |
| **External links** | 2 (x.com/SpaceX, starlink.com) |
| **Footer** | Careers, Updates, Privacy Policy, Suppliers, X social link |
| **Mobile** | Hamburger menu present, viewport meta set, responsive layout confirmed |
| **SSL** | HTTPS enforced |

**SEO risk summary:** The site is effectively invisible to search engines that don't execute JavaScript. No structured data, no meta tags, no semantic HTML signals. For a company of SpaceX's brand strength this is offset by massive direct/branded traffic, but any business without that level of brand recognition would lose significant organic search visibility with this setup.

---

*Generated by prospect-audit | impeccable-workflows*
