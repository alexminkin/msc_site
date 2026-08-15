# Implementation Roadmap

## Phase 1: Research And Content Structure

- Create content, reference, competitive, product, and planning folders.
- Conduct preliminary competitive analysis and product hypotheses.
- Keep unsupported business claims as `TODO_CONTENT`.

## Phase 2: Figma Layout

- Obtain or create editable Figma design file.
- Build public MVP pages, reusable service detail template, shared navigation, CTA blocks, and admin wireframes.
- Review at 320, 375, 768, 1024, and 1440 px.
- Wait for owner approval before code.

## Phase 3: App Scaffold

- Scaffold one Next.js Pages Router TypeScript application.
- Add Material UI theme, reusable public/admin components, React Hook Form, Zod, Prisma, Better Auth, and S3-compatible storage utilities.
- Keep public and admin areas clearly separated.

## Phase 4: Data And Admin

- Define Prisma schema for Better Auth entities, pages, services, FAQs, team members, media, settings, SEO, and contact submissions.
- Seed six MVP services and approved social URLs.
- Build admin CRUD and protected API routes.

## Phase 5: Public Website

- Implement approved Figma layout in code.
- Render SEO-critical public content server-side.
- Add contact flow, sitemap, robots, canonical metadata, structured data, and custom 404.

## Phase 6: QA And Launch Readiness

- Run install, lint, type check, production build, migrations, and seed.
- Verify responsive behavior, accessibility, protected admin routes, public routes, forms, links, sitemap, and robots.
