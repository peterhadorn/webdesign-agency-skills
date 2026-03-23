## Website Analysis: spacex.com

### What's Costing You Customers

**Your site is invisible to people who can't see it.** 31 out of 36 images have no descriptions for screen readers. That means visually impaired visitors -- including engineers, procurement officers, and government officials -- get a blank experience. Beyond the ethical issue, this is a legal liability under ADA compliance standards.

**Business visitors have no way to reach you.** There is no contact form, no email address, no phone number, and no "Request a Quote" button anywhere on the homepage. A satellite operator who wants to book a launch has exactly one obscure path: a tiny "Suppliers" link buried in the footer. Every visitor who can't figure out how to contact you is a lost opportunity.

**Your navigation is hidden from everyone.** The entire site menu is collapsed behind a hamburger icon, even on desktop screens with plenty of room. Visitors who want to learn about your vehicles, missions, or launch services have to discover that small icon exists first. Research shows hamburger menus reduce feature discoverability by up to 50%.

### What We'd Improve

1. **Add a clear "Book a Launch" or "Contact Us" path** visible on the homepage -- not buried in the footer. Business customers need to know how to start a conversation within 5 seconds.

2. **Show the navigation on desktop.** Keep the hamburger for mobile, but on wider screens, display the menu items directly. Visitors should see what you offer without having to click to find out.

3. **Add image descriptions to every photograph.** "Falcon 9 landing on a drone ship at sunset" takes 10 seconds to write and opens your site to millions of additional visitors while reducing legal risk.

4. **Add a proper page heading (H1) and meta description.** Search engines currently see no main heading and no page summary. This directly affects how you appear in Google results.

5. **Differentiate your calls to action.** Right now, "Explore," "Learn More," "Reserve Your Ride," "Join a Mission," and "Order Now" all look identical. Make the most important action -- likely Starlink orders or launch reservations -- visually stand out.

### What Caught Our Eye

**The photography is world-class.** Every section uses a breathtaking, real image that tells a story -- Mars at golden hour, Starship launching at dusk, Falcon 9 landing on a drone ship, an astronaut in profile, Starlink satellites in production. These are not stock photos. They communicate ambition, scale, and craftsmanship without saying a word.

**The one-message-per-screen layout is bold and effective.** Each full-viewport section delivers exactly one idea with one call to action. There is no clutter, no competing elements, no visual noise. This takes confidence to pull off, and SpaceX does it well.

**The brand voice is distinctive and consistent.** Headlines like "Making life multiplanetary" and "World's leading launch service provider" are clear, ambitious, and jargon-free. The copy is concise -- each section is one paragraph. It respects the visitor's time.

**The footer is clean and purposeful.** Careers, Updates, Privacy Policy, Suppliers -- nothing unnecessary. The X (Twitter) link makes sense given SpaceX's active social presence. This restraint is rare and appreciated.

### Technical Details (internal)

**Accessibility (Critical)**
- No H1 heading -- page starts at H2 level (WCAG 1.3.1 violation)
- 31 of 36 images have empty alt attributes (WCAG 1.1.1 violation)
- No skip-navigation link for keyboard users (WCAG 2.4.1 violation)
- No `<main>` landmark -- screen readers cannot jump to primary content
- Logo home link has no accessible name (img with empty alt inside link)
- White text overlaid on photographs without text-shadow or background overlay -- contrast ratio fails in lighter image regions (WCAG 1.4.3)

**SEO**
- Missing meta description tag -- Google will auto-generate a snippet
- Page title is just "SpaceX" -- could include mission-relevant keywords
- No structured data / schema markup detected

**Performance**
- 35 of 36 images use lazy loading (good)
- 1 above-the-fold image correctly loads eagerly
- Site uses Contentful CMS for image hosting (stripeassets.com CDN)
- Full-page consists of 5 full-viewport image sections -- large payload but appropriate for the design

**Design Pattern**
- Full-bleed cinematic sections with text overlay
- Dark theme throughout (black backgrounds, white/light typography)
- Minimal navigation: logo + hamburger on all viewports
- Consistent CTA pattern: uppercase text + right-arrow icon
- Footer: X social link, 4 text links, copyright
- No forms, no interactive elements beyond navigation and CTAs
- No client-side routing indicators (appears to be static/SSR)

**Anti-Patterns Verdict: PASS**
- No AI slop detected. No gradient text, glassmorphism, card grids, hero metrics, or generic SaaS patterns.
- The dark cinematic aesthetic is intentional and brand-appropriate for aerospace.
- Real photography, distinctive voice, and restrained design indicate human creative direction.
