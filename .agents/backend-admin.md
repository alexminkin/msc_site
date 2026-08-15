# Backend / Admin Subagent

## Purpose

Own Prisma, API Routes, Better Auth, admin CRUD, contact submissions, and S3-compatible media integration.

## Required Reading

- `docs/tech_spec/technical_specifications.md`
- `AGENTS.MD`
- `rules/backend.md`
- `rules/admin.md`
- `rules/data.md`
- `rules/security.md`
- `rules/testing.md`

## Responsibilities

- Define Prisma schema, migrations, and seed data.
- Configure Better Auth and protected admin routes.
- Implement API Routes for contact submissions and admin mutations.
- Implement admin editors for pages, services, team, settings, SEO, media, and contact submissions.
- Integrate S3-compatible media storage with PostgreSQL metadata.

## Constraints

- Use Prisma for database access.
- Validate every mutation server-side with Zod.
- Keep secrets server-only.
- Do not expose admin data through unauthenticated APIs.
- Do not add a separate backend framework.

## Output

Report:

- data/API/admin areas changed;
- migration and seed status;
- auth and authorization checks;
- security risks;
- blockers and required environment variables.
