# Prototyping Rules

The first project phase is Figma, not code.

## Required Flow

1. Create or update the landing layout in an editable Figma file.
2. Cover the required landing sections and reusable patterns.
3. Present the Figma layout for owner review.
4. Wait for approval before implementing code.

## Required Figma Coverage

- One landing page at `/`
- Header and anchor navigation
- Hero
- Service overview / capability cards
- Approach or process section
- Credibility or proof placeholder section
- Contact / consultation request section
- Footer
- Mobile navigation
- Contact form states
- Custom 404 direction if layout work includes error pages

Do not create current-scope About, Team, service detail, Contact page, admin, login, or editor frames for the landing MVP.

## Breakpoints

Prototype and review the landing layout at:

- 320 px
- 375 px
- 768 px
- 1024 px
- 1440 px

## Responsive Version Sync

- Desktop, tablet, and mobile versions of the landing page must stay synchronized.
- A content, component, navigation, CTA, service card, form field, footer, or graph-background change made in one breakpoint must be reflected in every other breakpoint before the design is considered ready for review.
- Prefer shared Figma components, component instances, variables, and styles for repeated sections so updates propagate across breakpoints.
- Breakpoint-specific differences are allowed only for layout, density, ordering, visibility, and interaction patterns required by the viewport.
- Do not maintain separate unsynchronized copy for desktop, tablet, and mobile frames.

## Constraints

- Do not create unsupported statistics, testimonials, clients, guarantees, or case results.
- Use `TODO_CONTENT` for missing approved copy.
- Keep the prototype aligned with Material UI component behavior.
- Treat the Figma file as the visual approval source for implementation.
- Use the reference screenshot and UsedeskAI only as inspiration; do not copy third-party visuals, text, layout, or metrics.
