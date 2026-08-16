# Prototyping Rules

The first project phase is Figma, not code.

## Required Flow

1. Create or update the website layout in an editable Figma file.
2. Cover the public MVP pages and reusable patterns.
3. Present the Figma layout for owner review.
4. Wait for approval before implementing code.

## Required Figma Coverage

- Home page
- About page
- Services overview
- Reusable service detail template
- Team page
- Contact page
- Header, footer, navigation, mobile navigation, service menu, and CTA blocks
- Admin wireframes for login, dashboard, editors, media, settings, SEO, and contact submissions

## Breakpoints

Prototype and review the layout at:

- 320 px
- 375 px
- 768 px
- 1024 px
- 1440 px

## Responsive Version Sync

- Desktop, tablet, and mobile versions of the same page must stay synchronized.
- A content, component, navigation, CTA, service card, form field, or footer change made in one breakpoint must be reflected in every other breakpoint before the design is considered ready for review.
- Prefer shared Figma components, component instances, variables, and styles for repeated sections so updates propagate across breakpoints.
- Breakpoint-specific differences are allowed only for layout, density, ordering, visibility, and interaction patterns required by the viewport.
- Do not maintain separate unsynchronized copy for desktop, tablet, and mobile frames.
- When Figma cannot automatically propagate a change across responsive frames, manually update the matching frames in the same task and record any unresolved sync risk.

## Constraints

- Do not create unsupported statistics, testimonials, clients, guarantees, or case results.
- Use `TODO_CONTENT` for missing approved copy.
- Keep the prototype aligned with the approved stack, especially Material UI component behavior.
- Treat the Figma file as the visual approval source for implementation.
