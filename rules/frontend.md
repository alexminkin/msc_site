# Frontend Rules

The landing MVP must be a single Next.js Pages Router app written in TypeScript.

## Stack

- Next.js Pages Router under `src/pages/`
- TypeScript
- Material UI
- React Hook Form
- Zod
- npm

Do not use App Router, Tailwind CSS, or another primary UI framework.

## Current Routes

Implement only these landing-version routes:

- `/`
- custom `404`

Do not implement `/about`, `/team`, `/contact`, `/services/*`, `/admin`, or authentication routes for the landing MVP.

## Rendering

- Render SEO-critical landing content server-side or statically at build time.
- Do not rely on client-side fetching for title, meta description, H1, service cards, primary CTA copy, or core section content.
- Store current landing content in source-controlled files until the specification approves database-backed editing.

## UI Rules

- Use Material UI as the primary component system.
- Centralize theme values for palette, typography, spacing, breakpoints, shape, shadows, and component overrides.
- Build landing sections for header, hero, services, approach, credibility placeholder, contact form, and footer.
- Use anchor navigation to landing sections, including `#services`, `#approach`, and `#contact`.
- Ensure desktop navigation, mobile navigation, and CTAs are keyboard accessible.
- Keep the dark-space luminous graph background readable, restrained, and synchronized with the approved Figma layout.

## Forms

- Use React Hook Form for form state.
- Use Zod schemas for client validation.
- Ensure `/api/contact` validates the same submitted data server-side.
- Show validation, pending, success, and generic failure states.
