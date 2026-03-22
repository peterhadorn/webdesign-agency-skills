## Website Analysis: subway.com

### What's Costing You Customers

1. **Your homepage is a wall of promotions -- visitors can't find what they came for.** The page opens with five stacked deal cards (the $6.99 footlong, bonus points, protein pockets, sub of the day, meal of the day), each competing for attention. A hungry customer who just wants to order food has to scroll past marketing before they can act. Every second of friction between "I'm hungry" and "I'm ordering" loses you sales -- especially on mobile where these cards dominate multiple screens.

2. **The menu section is completely broken -- it renders as invisible placeholder content.** The "Menu" heading sits above a grid of zero-width joiner characters (`&zwnj;`) instead of actual menu items. This means the entire menu preview section -- the most important content for a food business -- shows nothing. Visitors see blank space where food photos should be. If someone came to browse what you serve, they hit a dead end and leave.

3. **Multiple buttons and navigation elements have no accessible labels, locking out customers who use screen readers or voice control.** Four buttons in the hero area (refs e27, e28, e30, e31) have zero text and no aria-labels. The carousel "prev" and "next" buttons lack descriptive labels. Social media buttons in the footer use images but are buttons, not links, making their destination unclear. This affects an estimated 15-25% of users who rely on assistive technology, voice navigation, or have situational disabilities (e.g., driving and using voice commands to find nearby food).

---

### What We'd Improve

1. **Put "Order Now" and "Find a Location" front and center above the fold.** These are the two things hungry customers want. Right now, "Start Order" is a small link in the top nav competing with five other items. A prominent, impossible-to-miss order button at the top of the page would convert more visitors to orders.

2. **Fix the broken menu preview so visitors can see your food.** The menu grid renders as blank space. Showing appetizing food photography with names and prices directly on the homepage -- without requiring a click-through -- would keep visitors engaged instead of bouncing to a competitor's app.

3. **Reduce the promotional card overload from five cards to two.** Five rotating deal cards create decision paralysis. Feature your single best offer prominently, with a secondary deal below, and move the rest to a dedicated "Deals" page. Fewer choices = more action.

4. **Fix broken image assets that generate server errors.** Five image assets return 404 errors (close.png, close@2x.png, close@3x.png, 05-ui-icon-pickup@3x.png, share.png). These broken assets slow page load and may cause visual glitches in the ordering interface.

5. **Add proper labels to all interactive elements for accessibility compliance.** Unlabeled buttons and carousel controls should get descriptive aria-labels. This isn't just legal compliance (ADA) -- it's revenue from the significant percentage of customers using assistive technology.

---

### What Caught Our Eye

1. **The "Sub Club" loyalty program is well-positioned and clearly communicated.** The rewards banner with the "Introducing Sub Club" headline, a clear value proposition ("exclusive deals only available to members"), and dual CTAs ("Learn More" / "Join now") is effective. Loyalty programs drive repeat purchases, and this is given appropriate prominence.

2. **Deal pricing is specific and compelling.** "$6.99 ANY Footlong," "$3.99 Protein Pockets," "$4.99 Sub of the Day" -- these are concrete, easy-to-understand offers. No vague "save up to X%" language. Customers know exactly what they'll pay, which reduces hesitation.

3. **The catering section at the bottom speaks directly to a high-value use case.** "The perfect watch-party spread" with "Order Catering Now" targets group orders, which are typically 5-10x the value of individual orders. The copy is specific ("game-day spread") and the CTA is direct.

4. **Navigation structure is clean and focused.** Five main nav items (Menu, Find a Subway, Sub Club, Gift Cards, Catering & Groups) cover the key customer intents without overwhelming. The "Start Order" CTA is separated visually from navigation, which is a good pattern.

---

### Technical Details (internal)

#### Audit Findings

**Critical Issues:**

- **Broken content rendering**: The "Menu" section and a secondary content grid (refs e144-e166) render entirely as zero-width joiner characters. This appears to be a JavaScript rendering failure -- the content containers exist but no actual content loads into them. Two entire homepage sections are effectively blank.

- **Missing H1 heading**: The page has no H1 element. Headings start at H2 ("Get ANY Footlong for $6.99") and H3 ("Menu", "Deals & Promotions"). This hurts SEO and screen reader navigation. The page title "Home | Subway" is fine, but the document needs a primary heading.

- **Heading hierarchy violations**: H4 ("Introducing Sub Club") appears before any H2 or H3 in document order. The hierarchy jumps from H3 to H2 within the deals section, violating WCAG 1.3.1.

**High-Severity Issues:**

- **Unlabeled interactive elements**: 4+ buttons have no text content and no aria-label (carousel controls at refs e27, e28, e30, e31). The "prev"/"next" carousel buttons lack descriptive labels beyond their text.

- **5 broken image resources**: Server returns errors for close.png (all densities), 05-ui-icon-pickup@3x.png, and share.png. These are UI icons that likely affect the ordering overlay.

- **Cookie banner blocks content**: The OneTrust cookie dialog loads as a modal covering page content. While legally required, the implementation uses a full dialog that may trap keyboard focus.

- **Multiple `<main>` landmarks**: The page contains 3 nested `<main>` elements (one inside the banner, one as the primary content area, one nested within). Screen readers will be confused about which is the actual main content area. WCAG requires exactly one main landmark.

**Medium-Severity Issues:**

- **No lazy loading on images**: Food photography and promotional images load eagerly, increasing initial page weight. Below-fold images (catering box, deal cards 3-5) should use `loading="lazy"`.

- **Third-party script bloat**: The page loads LaunchDarkly (feature flags), Kount (fraud detection), Apptentive (feedback SDK), and OneTrust (cookies) -- all executing on the homepage where most visitors just want to browse or order. This adds significant JavaScript overhead.

- **Social media buttons instead of links**: Footer social icons (Facebook, Instagram, Twitter, YouTube, TikTok) are `<button>` elements with images, not `<a>` links. This means they likely open URLs via JavaScript, breaking right-click/open-in-new-tab and providing no href for accessibility tools.

- **"Franchise With Subway", "Subway Cares Foundation", "Partners:The Feed"** are buttons, not links -- same JavaScript navigation issue.

**Low-Severity Issues:**

- **Language selector is a raw `<select>` combobox** with only 2 options (US English, US Espanol). Functional but not styled consistently with the rest of the footer.

- **Copyright year range** "2023 - 2026" is fine but uses an en-dash inconsistently with other typography.

- **"Loading" text visible** (ref e176) suggests a spinner or loading state that persists or is not properly hidden after content loads.

#### Critique Findings

**Anti-Patterns Verdict: PASS (not AI-generated)**
This is clearly a professionally built corporate website, not AI-generated. The design has Subway's established brand identity, custom photography, and a commercial ordering system integration. No gradient text, glassmorphism, or generic AI color palettes. The issues are typical of large enterprise websites maintained by multiple teams over years -- not AI slop.

**Visual Hierarchy:**
The page lacks a clear primary action above the fold. The "Start Order" button is small and positioned in the navigation bar. The first thing visitors see is the Sub Club loyalty banner, not a path to ordering food. For a QSR (quick-service restaurant), the ordering flow should dominate.

**Information Architecture:**
The page structure is: Hero/Carousel -> Sub Club -> Menu (broken) -> Deals (5 cards) -> Content grid (broken) -> Catering -> Footer. Two of these sections are broken, leaving the page feeling sparse. The deals section does most of the heavy lifting.

**Emotional Resonance:**
The page feels promotional rather than appetizing. A food business homepage should make you hungry. Instead, it reads like a coupon book -- deal after deal after deal. The food photography that does load (sub images in deal cards) is well-shot but secondary to pricing text.

**Composition:**
The promotional card carousel creates a monotonous rhythm -- every card has the same layout (heading, description, terms button, CTA, image). By the third card, visitors are pattern-blind. Varying the presentation would maintain engagement.
