# Contact API / Future Admin Subagent

## Purpose

Own landing contact API validation and safe submission handling. Admin, auth, database, and media infrastructure are future-only for the current landing MVP.

## Required Reading

- `docs/tech_spec/landing_technical_specifications.md`
- `AGENTS.MD`
- `rules/backend.md`
- `rules/admin.md`
- `rules/data.md`
- `rules/security.md`
- `rules/testing.md`

## Responsibilities

- Implement shared Zod validation for contact submissions.
- Implement `/api/contact` with method checks, validation, abuse protection, safe responses, and approved delivery handling.
- Document required contact provider environment variables.
- Review secrets handling and error behavior.

## Out Of Scope

- Prisma schema, migrations, and seed data.
- Better Auth and protected admin routes.
- Admin CRUD and editor UI.
- PostgreSQL persistence.
- S3-compatible media storage.
- `/api/admin/*` and `/api/auth/*`.

## Constraints

- Validate every mutation server-side with Zod.
- Keep secrets server-only.
- Do not add a separate backend framework.
- Do not expose stack traces, provider responses, or private contact details in API errors.

## Output

Report:

- contact API areas changed;
- validation and abuse-protection behavior;
- security risks;
- blockers and required environment variables.
