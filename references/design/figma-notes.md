# Figma Notes

## Current Status

- Editable Figma design URL: `https://www.figma.com/design/9ZXhf3VkhxszM2P98ZDUVp`
- Current synchronized landing desktop frame: `Main page_v2 / Dark Space 1440` (`39:2`)
- Current synchronized landing tablet frame: `Main page_v2 / Dark Space Tablet 768` (`40:2`)
- Current synchronized landing mobile 375 frame: `Main page_v2 / Dark Space Mobile 375` (`40:127`)
- Current synchronized landing mobile 320 frame: `Main page_v2 / Dark Space Mobile 320` (`40:248`)
- Previous synchronized landing frames: `Main page_v1` (`23:2`), `Main page_v1 / Tablet 768` (`32:2`), and `Main page_v1 / Mobile 375` (`30:2`)
- Current layout status: v2 dark/space landing layout is prepared for owner review; it is not approved for code implementation until owner explicitly approves it.
- Current design direction note frame: `Design note / UsedeskAI-inspired dark space direction` (`40:368`)
- Published Figma Site URL reviewed: `https://www.figma.com/site/qc1wgQnVsmSjWD7gKmodGw/MinkinSpace-Consulting`
- Connector status: published `/site/` URL is not usable for direct Figma design-node edits.

## Current Landing Scope

Required landing coverage:

- Header and anchor navigation
- Hero
- Service overview / capability cards
- Approach or process section
- Credibility or proof placeholder section
- Contact / consultation request section
- Footer
- Mobile navigation
- Contact form states

Do not treat About, Team, service detail pages, standalone Contact page, admin wireframes, or editor screens as current landing MVP requirements.

## Required Breakpoints

- 320 px
- 375 px
- 768 px
- 1024 px
- 1440 px

## Responsive Sync Rule

- `Main page_v2 / Dark Space 1440`, `Main page_v2 / Dark Space Tablet 768`, `Main page_v2 / Dark Space Mobile 375`, and `Main page_v2 / Dark Space Mobile 320` must be treated as synchronized versions of the same landing page.
- Copy, navigation, CTA, cards, form fields, footer content, colors, typography decisions, and reusable visual patterns must be updated across all versions in the same design pass.
- Breakpoint-specific differences are allowed only for responsive layout, density, ordering, visibility, and interaction behavior.
- Figma does not automatically mirror arbitrary edits between separate responsive frames unless shared components, variables, or styles are used. When an edit cannot propagate automatically, update the matching frames manually before review.

## Approval Gate

Code implementation starts only after owner approval of the editable Figma landing layout.

## Current Redesign Notes

- Reference inspiration: `https://usedeskai.ru` dark SaaS landing rhythm, sticky nav, short numbered sections, hero product/mockup area, glow accents, conversion rhythm, and footer clarity.
- Required adaptation: dark space consulting/SaaS palette, MinkinSpace Forward Orbit direction, landing anchor navigation, six approved service directions, Material UI-compatible component behavior, no copied UsedeskAI text, screenshots, proprietary assets, pricing claims, metrics, or case claims.
- Background visual direction: use an original dark blue node-and-connection technical field with luminous graph structure. The graph must be visible through the page while scrolling, but restrained enough to preserve WCAG-oriented text contrast and avoid dense dashboard clutter.
- Hero graph update, 2026-08-17: added a dedicated `Luminous graph / hero density boost` layer to the synchronized v2 desktop, tablet, mobile 375, and mobile 320 frames. The update adds a modest extra node/edge cluster in the hero area while keeping density restrained and preserving readability.
- Header update, 2026-08-17: set synchronized v2 header background to `#0b2342`, removed `Home` from the menu, changed remaining menu labels to lowercase Montserrat Light in white, and replaced the previous mark/wordmark with the supplied logo image and supplied MinkinSpace Consulting company-name image.
- Missing unapproved copy, proof, metrics, cases, contact details, and team material remains marked as `TODO_CONTENT`.
