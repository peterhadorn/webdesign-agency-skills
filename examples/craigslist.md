## Website Analysis: craigslist.org

**Score: 4/10** — Lightning fast and distraction-free, but the dated interface and impossible mobile experience are pushing users to modern alternatives.

### What's Costing You Customers

**1. Your site looks abandoned.** Craigslist's homepage has not meaningfully changed its design since the early 2000s. No images, no color, no visual cues -- just walls of purple text links on a plain white background. First-time visitors (especially younger users) instinctively associate this aesthetic with spam, phishing, or a site that is no longer maintained. People who would use your platform leave before they ever post a listing because the site does not look trustworthy enough to enter personal information or spend money on a paid posting.

**2. New visitors have no idea where to start.** The homepage presents roughly 200 links at once across six dense columns with no visual priority. Community, housing, services, for sale, jobs, discussion forums, gigs, resumes -- all given equal visual weight. A person looking to rent an apartment sees the same small purple text as someone looking for a used bicycle or a philosophy debate forum. There is no guidance, no "start here," no prominent search experience. Every second a visitor spends scanning and deciphering your link wall is a second closer to them opening Facebook Marketplace or Zillow instead.

**3. On a phone, the experience is painful.** The category links are tiny text packed tightly together. On a mobile device, tapping "apartments" without accidentally hitting "parking / storage" or "office / commercial" right next to it is a genuine challenge. The sub-region buttons at the top ("sfc", "sby", "eby", "pen", "nby", "scz") are cryptic abbreviations that mean nothing to someone who just moved to the area. Mobile users make up the majority of web traffic today, and your site actively punishes them.

### What We'd Fix (in priority order)

1. **Increase tap target sizes for mobile.** Every clickable link and button should be large enough to tap comfortably on a phone screen. Right now, the dense link lists are a usability hazard on any device without a mouse. · _Small project_

2. **Make search the centerpiece.** The search box is a small, unstyled input tucked into the left sidebar. For a site built on finding things, search should be large, central, and inviting. This single change could dramatically increase engagement from first-time visitors. · _Small project_

3. **Give the top 3 categories real prominence.** Housing, jobs, and for-sale are what bring people to Craigslist. Make these visually dominant with larger text, icons, or distinct sections. The long tail of subcategories can live one click deeper. · _Larger project_

4. **Spell out the sub-regions.** Replace "sfc", "sby", "eby" with "San Francisco", "South Bay", "East Bay." New residents and tourists should not need a decoder ring to use your site. · _Quick win_

5. **Add a minimal visual layer.** Simple category icons, slightly larger touch targets, and basic spacing improvements would signal "this site is actively maintained" without sacrificing the utilitarian identity. · _Larger project_

### What Caught Our Eye

- **Page speed is exceptional.** Craigslist loads almost instantly. No bloated JavaScript frameworks, no third-party trackers, no cookie banners, no autoplay videos. In an era of 5-second load times and consent popups, this is a genuine competitive advantage that most modern websites would envy.

- **Zero distractions from the content.** There are no ads on the homepage, no pop-ups, no newsletter signup modals, no chatbots. Users come to find or post listings, and the homepage does not put anything between them and that goal. This restraint is rare and valuable.

- **The information architecture is comprehensive.** Every conceivable category is represented and logically grouped. Community, housing, services, for-sale, jobs, gigs, resumes -- the taxonomy is thorough and well-organized for users who already know what they are looking for.

- **The event calendar is a thoughtful touch.** A simple, functional calendar sits in the sidebar for browsing local events by date. It is modest, unobtrusive, and genuinely useful -- exactly the kind of feature that rewards regular visitors.

### Technical Details (internal)

**Accessibility**
- No semantic HTML landmarks detected. The page uses `<div>` elements throughout instead of `<nav>`, `<main>`, `<header>`, `<footer>`. Screen readers cannot navigate by landmark regions. Violates WCAG 1.3.1 (Info and Relationships).
- Heading hierarchy is flat: a single H1 ("craigslist") followed by H2s for each category section. No H3s or deeper levels for subcategories. Structure is acceptable but minimal.
- Search input has a placeholder ("search craigslist") but no associated `<label>` element or `aria-label`. Screen reader users may not understand the input's purpose. WCAG 1.3.1 / 4.1.2 violation.
- Sub-region buttons ("sfc", "sby", "eby", "pen", "nby", "scz") have no `aria-label` or `title` to explain what the abbreviations mean. Accessibility and usability issue.
- The "faves" link appears to use `href=""` (empty string), which is a non-functional link that confuses assistive technology and provides no destination context.
- Calendar table lacks `<caption>` and uses minimal semantic markup. Days of the week use short abbreviations (S, M, T, W, T, F, S) without `<abbr>` elements.

**Responsive Design**
- Touch targets throughout the page are critically undersized. The dense link columns have line heights of approximately 18-20px with minimal padding. On mobile, these are well below the 44x44px minimum recommended by WCAG 2.5.5 (Target Size).
- Sub-region filter buttons ("sfc", "sby", etc.) appear to be roughly 30x20px -- far too small for reliable mobile tapping.
- The multi-column layout (left sidebar + center content + right sidebar) does not appear to collapse for narrow viewports, likely causing horizontal scrolling or extremely compressed columns on phones.
- The language `<select>` dropdown in the top-right corner is small and isolated, easily missed on any screen size.

**Performance**
- Minimal external resources: the page loads very few stylesheets and scripts. No heavy JavaScript frameworks detected. This is a strength -- the page likely achieves sub-1-second Time to Interactive.
- No images on the homepage (except small charity icons), eliminating image optimization concerns entirely.
- No third-party analytics, tag managers, or advertising scripts visible. Exceptional for privacy and performance.

**Design / UX**
- Typography is browser-default sans-serif with no custom font loading. Functional but generic.
- Color palette is limited to purple links (#0000FF or similar), black text, and white background. No brand colors, no visual differentiation between sections.
- No hover states visible beyond default browser link underlines. No visual feedback on interactive elements beyond cursor changes.
- The "post an ad" call-to-action (a primary revenue driver) is a small green text link in the left sidebar, competing with dozens of other links for attention.
- The "craigslist charitable" section with small emoji-like icons is visually disconnected from the rest of the page and its purpose is unclear without clicking.
- Footer is minimal (help, safety, privacy, terms, about, app, sitemap) -- functional and appropriate.
- The page title "craigslist: SF bay area jobs, apartments, for sale, services, community, and events" is well-structured for SEO with geographic and categorical keywords.
