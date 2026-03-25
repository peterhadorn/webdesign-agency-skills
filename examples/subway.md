## Website Analysis: subway.com

**Score: 5/10** — Great food photography and strong brand, but promotional overload and a cookie banner blocking the hero are costing conversions.

### What's Costing You Customers

**1. Your homepage fights itself for attention.** There are 8+ buttons all screaming "click me" at the same time -- order buttons, sign-up buttons, deal buttons, loyalty buttons. When everything is urgent, nothing is. Visitors freeze up and leave. A hungry customer who just wants to place an order has to mentally sort through a wall of promotions to find the "Start Order" button hiding in the top corner. Every second of confusion is a lost sale.

**2. Your best promotion is hidden behind a legal popup.** The very first thing every new visitor sees is a cookie consent banner covering your hero section. That "$4.99 Sub of the Day" deal you paid to design and promote? Invisible. Most people dismiss the popup without ever seeing what was behind it. You are paying for homepage real estate that nobody sees.

**3. Too many deals dilute all of them.** The page shows five simultaneous promotions ($6.99 Any Footlong, 100 bonus points, $3.99 Protein Pockets, $4.99 Sub of the Day, $6.99 Meal of the Day) plus a loyalty signup and a catering push. Research consistently shows that fewer, stronger offers outperform a buffet of choices. When a customer sees five deals, they compare and hesitate. When they see one great deal, they act.

### What We'd Fix (in priority order)

1. **Move the cookie banner out of the way.** A small bar at the bottom of the screen (industry standard) instead of a popup covering your best content. Your hero promotion starts working for you on every single visit. · _Quick win_

2. **One clear action per screen.** A visitor should know within 2 seconds what to do: order food. Everything else (deals, loyalty, catering) is secondary. This alone could measurably increase online orders. · _Larger project_

3. **Cut the promotions in half.** Feature one headline deal prominently, show 2-3 others below it, and rotate them. Fewer choices, faster decisions, more orders. · _Small project_

4. **Make the menu section actually useful.** Show your most popular items with names and prices, or remove the section and link to the full menu. Half-measures waste prime page space. · _Small project_

5. **Fix the catering pitch.** The "perfect watch-party spread" copy ties your catering business to game days. A year-round message ("Feed your next group for less") works every day, not just on Sundays in the fall. · _Quick win_

### What Caught Our Eye

- **The food photography is excellent.** The subs look fresh, overstuffed, and genuinely appetizing. This is your strongest visual asset and it is working hard for you. Do not change it.

- **Pricing is bold and scannable.** When a deal-conscious customer reaches the promotions section, the prices ($6.99, $4.99, $3.99) are large, prominent, and easy to compare at a glance. This is smart design for a value-driven audience.

- **Brand identity is rock solid.** The green-and-yellow palette is unmistakably Subway. There is no confusion about whose site this is. The logo, colors, and overall feel are consistent and professional.

- **Loyalty program is well-positioned.** The Sub Club banner is visible early on the page with a clear value proposition ("exclusive deals only for members") and a direct signup button. Loyalty drives repeat business, and you are promoting it in the right place.

### Technical Details (internal)

**Accessibility (Critical)**
- No H1 element on the page. Heading hierarchy is inverted: H4 appears before H3, and H2s are nested inside H3 sections. Violates WCAG 1.3.1 (Info and Relationships). Hurts SEO ranking.
- Multiple unlabeled buttons throughout the page (carousel arrows, floating action buttons) -- no text, aria-label, or title attribute. Screen reader users cannot interact with these controls. WCAG 4.1.2 violation.
- Three separate `<main>` landmark elements on one page. Screen readers expect a single main landmark. WCAG 1.3.1 violation.
- Zero-width non-joiner characters (`&zwnj;`) flood the Menu and Top Picks sections in the DOM, creating confusing screen reader output.
- Social media icons in the footer are `<button>` elements instead of `<a>` links -- users cannot right-click to open in a new tab or see the destination URL.

**Performance**
- 6 console errors on page load: missing image assets (close.png, close@2x.png, close@3x.png, share.png, pickup icon). Failed resource loads degrade perceived performance.
- Heavy third-party script load: LaunchDarkly (feature flags), Apptentive (feedback SDK), Kount (fraud detection), Adobe Launch (tag manager) all initialize on the homepage. Each adds to Time to Interactive.
- Menu and Top Picks sections appear to lazy-load content via JavaScript but render empty placeholder elements (`&zwnj;`) on initial paint, causing layout shift.

**UX/Structure**
- Cookie consent dialog overlays the hero section on first visit, blocking the primary promotional content.
- Carousel navigation: "prev" button starts disabled with no visual explanation; neither prev/next button has an accessible label.
- `javascript:void(0)` used as href for "Cookie & Ad Settings" link instead of a semantic `<button>` element.
- Catering section copy ("watch-party spread," "game-day") is seasonally bound and likely stale outside football season.
- Language selector is a bare `<select>` dropdown labeled only "language" -- functional but poorly integrated.
- Page title "Home | Subway" is generic; a more descriptive title would improve search visibility.
