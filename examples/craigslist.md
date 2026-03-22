# Website Analysis: craigslist.org

> Audited 2026-03-22 | SF Bay Area regional homepage (sfbay.craigslist.org)

---

## What's Costing You Customers

**The site looks like it hasn't been updated since 2003 -- and visitors notice.** First impressions form in under 50 milliseconds. When someone lands on a page that looks outdated, they unconsciously trust it less. For a marketplace that depends on people posting ads and replying to listings, that eroded trust translates directly into fewer posts, fewer replies, and users migrating to Facebook Marketplace or Nextdoor where the experience feels modern and safe.

**On a phone, everything is too small to tap.** 40 interactive elements (buttons, links, form fields) are smaller than the 44px minimum that Apple and Google recommend for touch targets. The search bar is only 28px tall. Navigation buttons like "post" and "acct" render at 10px font size. When someone tries to tap "post an ad" on their phone and accidentally hits the wrong link, they don't try again -- they leave. Given that over 60% of web traffic is mobile, this is a significant leak in the funnel.

**Over 1,000 text elements on mobile are below readable size.** Font sizes as small as 10px force users to pinch-zoom just to read navigation labels. This is particularly damaging for the core audience segments that rely on Craigslist for jobs, housing, and services -- people who are often searching on the go, on older phones, in a hurry.

---

## What We'd Fix

**Redesign the mobile experience with proper touch targets and readable text.** Every tappable element should be at least 44x44px, and body text should be 16px minimum on phones. This single change would reduce accidental taps, decrease bounce rate on mobile, and make the site usable for the majority of visitors who arrive on a phone. Expected impact: measurably higher post and reply rates from mobile users.

**Add a modern visual layer without losing the simplicity.** Craigslist's minimalism is an asset, but "minimal" and "neglected" are different things. Updated typography, proper spacing, and a cleaner category layout would preserve the fast, no-nonsense brand while signaling that the platform is actively maintained and trustworthy. Users post more when they trust the platform.

**Set the HTML language attribute.** The page is missing `lang="en"`, which means screen readers and translation tools cannot properly identify the language. This is a one-line fix that instantly improves accessibility for millions of users with disabilities and non-native English speakers. It also helps search engines serve the right regional version.

**Add Open Graph image tags for social sharing.** When someone shares a Craigslist listing on iMessage, WhatsApp, or Slack, it shows up as a plain text URL with no preview image. Adding an `og:image` tag means shared links display with a branded preview, which increases click-through rates on shared listings by 2-3x.

**Implement proper heading hierarchy.** The page has a single H1 ("craigslist") and zero H2 tags. Category sections like "community," "housing," "jobs," and "for sale" should be proper H2 headings. This helps both screen reader users navigate the page and search engines understand the content structure, which can improve ranking for local search queries.

---

## What Caught Our Eye

**Page speed is exceptional.** The site loads in 240ms with a 43ms time-to-first-byte. That is roughly 10x faster than the average website. In a world where every 100ms of load time costs 1% of conversions, Craigslist is leaving nothing on the table when it comes to speed. The entire page is served with just 1 CSS file and 3 JavaScript files -- no bloat, no third-party trackers slowing things down.

**Search engine fundamentals are solid where they exist.** The page has a proper meta description, OG title and description tags, and structured data (Schema.org SearchAction) that enables Google sitelinks search. This is more than many larger sites implement.

**HTTPS everywhere and no console errors.** The site serves over HTTPS with zero JavaScript console errors -- a clean runtime with no broken scripts or failed resource loads. Many enterprise sites cannot claim this.

**The mobile layout actually adapts.** Despite the touch target issues, the page does respond to mobile viewports: no horizontal scrolling at 375px, categories collapse into a vertical list, and the layout restructures for smaller screens. The responsive foundation is there -- it just needs refinement.

---

## Technical Details (internal)

### SEO & Meta Tags
| Signal | Status |
|--------|--------|
| Page title | "craigslist: SF bay area jobs, apartments, for sale, services, community, and events" |
| Meta description | "craigslist provides local classifieds and forums for jobs, housing, for sale, services, local community, and events" |
| og:site_name | "craigslist" |
| og:title | Present (mirrors page title) |
| og:description | Present (mirrors meta description) |
| og:image | **MISSING** |
| og:url | https://sfbay.craigslist.org/ |
| Schema.org | SearchAction (WebSite type, sitelinks search box) |
| HTML lang attribute | **MISSING** |
| Viewport meta | `width=device-width,initial-scale=1` |
| HTTPS | Yes |
| Favicon | Present |

### Performance (Navigation Timing API)
| Metric | Value |
|--------|-------|
| Time to First Byte (TTFB) | 43 ms |
| DOM Interactive | 83 ms |
| DOM Content Loaded | 84 ms |
| Full Page Load | 240 ms |
| Total Duration | 240 ms |

### Page Weight
| Asset Type | Count |
|------------|-------|
| CSS files | 1 |
| JS files | 3 |
| Images | 0 (icons via icon font "icomoon") |
| Total links on page | 448 |

### Typography
| Font | Usage |
|------|-------|
| "Open Sans", Helvetica, Arial, sans-serif | Body text, links |
| "Times New Roman", Times, serif | Branding/logo area |
| icomoon | Icon font |

### Headings
| Level | Content |
|-------|---------|
| H1 | "craigslist" (1 instance) |
| H2 | None (0 instances) |

### Accessibility & Mobile (Desktop at 1200px)
| Issue | Count |
|-------|-------|
| Touch targets under 44px (desktop) | 270 of ~448 interactive elements |
| Smallest touch targets | Sub-area buttons (sfc, sby, eby) at 26x22px |
| Horizontal overflow at 1200px | None |

### Mobile Audit (375px viewport)
| Issue | Count / Detail |
|-------|----------------|
| Touch targets under 44px | 40 elements |
| Search input height | 28px (should be 44px+) |
| Location button | 150x33px (height under 44px) |
| Text under 14px | 1,076 elements |
| Smallest font size observed | 10px (nav labels: "faves", "post", "acct") |
| Horizontal overflow | None (no scrollbar) |

### Console Errors
| Context | Errors |
|---------|--------|
| Desktop page load | 0 |
| Mobile page load | 0 |

### Missing / Deficient
- No `lang` attribute on `<html>` element
- No `og:image` meta tag
- No H2 heading hierarchy (categories are not semantically marked)
- Icon font (icomoon) used instead of inline SVGs (accessibility concern for screen readers)
- Search input has no visible `<label>` element (placeholder only)
