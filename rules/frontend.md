# Frontend Rules

The application must be a single Next.js Pages Router app written in TypeScript.

## Stack

- Next.js Pages Router under `src/pages/`
- TypeScript
- Material UI
- React Hook Form
- Zod
- npm

Do not use App Router or Tailwind CSS.

## Public Routes

Implement these MVP routes:

- `/`
- `/about`
- `/services`
- `/services/business-process-automation`
- `/services/ai-pre-sales`
- `/services/it-infrastructure-audit`
- `/services/marketing-ai-analysis`
- `/services/ai-search-geo`
- `/services/social-marketing`
- `/team`
- `/contact`
- custom `404`

## Rendering

- Render public business-critical and SEO-critical content server-side.
- Use `getServerSideProps` for database-backed public content unless the spec is changed.
- Do not rely on client-side hydration for titles, meta descriptions, H1 content, services, contact data, or primary page copy.

## UI Rules

- Use Material UI as the primary component system.
- Centralize theme values for palette, typography, spacing, breakpoints, shape, shadows, and component overrides.
- Keep header, footer, CTA, service cards, process steps, FAQ, team cards, and form components reusable.
- Ensure navigation, services dropdown, and mobile drawer are keyboard accessible.
- Keep public and admin components clearly separated.

## Forms

- Use React Hook Form for form state.
- Use Zod schemas for client validation.
- Ensure API routes validate the same submitted data server-side.
