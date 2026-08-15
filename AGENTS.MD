# MinkinSpace Consulting Agent Guide

This repository is the working base for the MinkinSpace Consulting corporate website.

## Source Of Truth

Before making any code, design, infrastructure, or content change, read:

1. `docs/tech_spec/technical_specifications.md`
2. This `AGENTS.MD`
3. The relevant files in `rules/`
4. The relevant subagent definitions in `.agents/`, when delegating runtime subagent work
5. Relevant approved source material in `content/` and `references/design/`, when present

If instructions conflict, follow the newest explicit user instruction first, then the approved technical specification.

## Fixed Stack

Do not replace or migrate away from these technologies without explicit owner approval:

- Next.js
- Pages Router
- TypeScript
- Material UI
- React Hook Form
- Zod
- Next.js API Routes
- Better Auth
- Prisma ORM
- PostgreSQL
- S3-compatible Object Storage
- npm

Do not introduce App Router, Tailwind CSS, Redux, NestJS, Express as a separate server, GraphQL, tRPC, Redis, microservices, Kubernetes, or an external CMS for the MVP.

## Mandatory Workflow

The site must be developed in this order:

1. Build design and visual structure in Figma.
2. Wait for owner approval or disapproval.
3. Move to code only after approval.

Do not start implementation from an unapproved layout. If content is missing but non-blocking, mark it as `TODO_CONTENT` rather than inventing claims, statistics, testimonials, clients, or results.

The current editable Figma layout reference is tracked in `references/design/figma-notes.md`. Treat it as a design reference until owner approval is explicitly recorded.

## Content And References

- `content/` is reserved for owner-approved copy, content drafts, service text, team material, legal text, media notes, and launch content sources.
- `references/design/` is reserved for design references, benchmark screenshots, visual research, UI examples, brand inspiration, and notes about current design best practices.
- Treat files in these folders as reference inputs, not as automatic implementation authority.
- Do not copy third-party designs, images, text, or proprietary material directly into the product unless rights and approval are clear.
- Prefer current, high-quality, accessible, responsive design practices, but keep final decisions aligned with the approved Figma layout and technical specification.
- Do not invent business claims from references. Use `TODO_CONTENT` for missing approved content.

## Required Agent Behavior

- Inspect the current repository before changing files.
- Reuse existing conventions and components once the app exists.
- Keep public and admin code clearly separated.
- Store editable business content in PostgreSQL.
- Use Prisma for database access.
- Use Better Auth for admin authentication.
- Use React Hook Form and Zod for forms and API validation.
- Use Material UI as the only primary UI library.
- Store media files in S3-compatible storage, with PostgreSQL storing only metadata.
- Keep secrets server-only and out of committed files.
- Validate every mutation server-side.
- Preserve accessibility, responsive behavior, SEO, and GEO requirements.
- Record unresolved implementation decisions in `docs/open-questions.md` once that file exists.

## Rule Index

- `rules/prototyping.md` - Figma-first workflow and approval gates.
- `rules/design.md` - brand, layout, accessibility, and responsive design rules.
- `rules/frontend.md` - public and admin frontend rules.
- `rules/backend.md` - API, validation, auth, and server behavior.
- `rules/seo.md` - SEO and AI Search / GEO rules.
- `rules/admin.md` - admin panel behavior and security.
- `rules/data.md` - Prisma data model and seed requirements.
- `rules/security.md` - security, secrets, rate limiting, and uploads.
- `rules/testing.md` - checks and acceptance testing.
- `rules/deployment.md` - remote launch requirements.

## Subagent Index

- `.agents/README.md` - limited runtime subagent model and delegation rules.
- `.agents/design-figma.md` - Figma layout, visual structure, brand consistency, responsive design, and approval readiness.
- `.agents/frontend.md` - public Pages Router UI, Material UI components, responsive layout, navigation, forms, and SSR integration.
- `.agents/backend-admin.md` - Prisma, API Routes, Better Auth, admin CRUD, contact submissions, and S3 media.
- `.agents/seo-geo.md` - SEO metadata, canonical URLs, sitemap, robots, structured data, semantic headings, and GEO review.
- `.agents/qa-deployment.md` - verification, accessibility, responsive QA, protected API checks, deployment checklist, and launch readiness.

## Tooling Index

- `.agents/skills/` contains installed Agent Skill artifacts managed by the skills CLI. Keep each installed skill as a complete directory with its `SKILL.md` and companion files.
- `skills-lock.json` records installed Agent Skills and should be kept in sync with `.agents/skills/`.
- `mcp/` should not exist unless real MCP-related artifacts are installed or required.
- Do not recreate top-level `skills/` for project rules or notes; use `rules/` or approved project docs instead.
- Document project-specific tool guidance in `rules/` or approved project docs instead.

Never commit credentials, tokens, private keys, database URLs, S3 secrets, production admin passwords, or private MCP connection details.
