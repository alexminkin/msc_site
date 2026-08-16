# Implementation Roadmap

## Phase 1: Landing Research And Content Structure

- Keep competitive analysis, product hypotheses, and service notes as reference inputs.
- Move final approved copy to `content/approved/`.
- Keep unsupported business claims as `TODO_CONTENT`.

## Phase 2: Figma Landing Layout

- Use the editable Figma file as the visual approval source.
- Finalize the dark-space landing layout with luminous graph background.
- Review at 320, 375, 768, 1024, and 1440 px.
- Wait for owner approval before code.

## Phase 3: App Scaffold

- Scaffold one Next.js Pages Router TypeScript application.
- Add Material UI theme, landing components, React Hook Form, and Zod.
- Do not add Better Auth, Prisma, PostgreSQL, S3 storage, or admin directories.

## Phase 4: Landing Website

- Implement the approved Figma layout at `/`.
- Add custom `404`.
- Render SEO-critical landing content statically or server-side.
- Add sitemap, robots, favicon, canonical metadata, Open Graph metadata, and structured data where visible content supports it.

## Phase 5: Contact Flow

- Implement shared Zod validation for the contact form and `/api/contact`.
- Add server-side abuse protection and safe typed responses.
- Connect to an approved email provider, webhook, or approved temporary fallback.

## Phase 6: QA And Launch Readiness

- Run install, lint, type check, production build, responsive, accessibility, SEO, and contact API checks.
- Verify forbidden routes resolve to the custom `404`.
- Verify production secrets and contact submission handling before launch.
