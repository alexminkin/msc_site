# Figma Notes

## Current Status

- Editable Figma design URL: `https://www.figma.com/design/9ZXhf3VkhxszM2P98ZDUVp`
- Current MVP prototype page: `MVP prototype coverage`
- Current public Home frame ID: `2:2`
- Current public Home frame canvas position: separate left-side location at `x=-1700`, `y=80`
- Current synchronized landing desktop frame: `Main page_v1` (`23:2`)
- Current synchronized landing mobile frame: `Main page_v1 / Mobile 375` (`30:2`)
- Current synchronized landing tablet frame: `Main page_v1 / Tablet 768` (`32:2`)
- Current reusable service detail template frame ID: `2:122`
- Current contact submissions admin wireframe ID: `3:64`
- Archived test layouts: deleted from editable Figma file
- Current layout status: MVP prototype coverage has been updated with an ExactFarming-inspired blue public-site redesign for owner review; not approved for code implementation until owner explicitly approves it.
- Current design direction note frame: `Design note / ExactFarming-inspired blue direction`
- Published Figma Site URL reviewed: `https://www.figma.com/site/qc1wgQnVsmSjWD7gKmodGw/MinkinSpace-Consulting`
- Connector status: published `/site/` URL is not usable for direct Figma design-node edits.

## Required Layout Coverage

- Home page
- About page
- Services overview
- Reusable service detail template
- Team page
- Contact page
- Header, footer, navigation, mobile navigation, service menu, and CTA blocks
- Admin wireframes for login, dashboard, editors, media, settings, SEO, and contact submissions

Coverage status: frames have been added to the editable Figma file. Remaining gate is owner review and approval.

## Required Breakpoints

- 320 px
- 375 px
- 768 px
- 1024 px
- 1440 px

## Responsive Sync Rule

- `Main page_v1`, `Main page_v1 / Tablet 768`, and `Main page_v1 / Mobile 375` must be treated as synchronized versions of the same page.
- Copy, navigation, CTA, cards, form fields, footer content, colors, typography decisions, and reusable visual patterns must be updated across all three versions in the same design pass.
- Breakpoint-specific differences are allowed only for responsive layout, density, ordering, visibility, and interaction behavior.
- Figma does not automatically mirror arbitrary edits between separate responsive frames unless shared components, variables, or styles are used. When an edit cannot propagate automatically, update the matching frames manually before review.

## Approval Gate

Code implementation starts only after owner approval of the editable Figma layout.

## Current Redesign Notes

- Reference inspiration: ExactFarming-style SaaS/product clarity, section rhythm, segmented cards, and abstract system visual treatment.
- Required adaptation: blue consulting/SaaS palette, MinkinSpace Forward Orbit direction, no copied ExactFarming text, screenshots, agriculture imagery, green palette, or proprietary assets.
- Missing unapproved copy, proof, metrics, cases, contact details, and team material remains marked as `TODO_CONTENT`.
