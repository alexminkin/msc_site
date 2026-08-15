# Data Rules

Prisma schema is the source of truth for relational data models and migrations.

## Required Entities

- Better Auth user/session/account entities
- `Page`
- `Service`
- `ServiceFaq`
- `TeamMember`
- `Media`
- `SiteSettings`
- `ContactSubmission`

## Required Behavior

- Public content intended for routine editing must live in PostgreSQL.
- Six MVP services must exist as seed data.
- Site settings seed must include the approved LinkedIn and Instagram URLs.
- Service pages must be data-driven and use one reusable page structure.
- Services and team members must support publication status and display order.
- Editable core entities must include `createdAt` and `updatedAt`.
- Use `updatedByUserId` where practical for administrative changes.

## Content Rules

- Do not duplicate business-critical settings across hardcoded constants.
- Store social URLs in `SiteSettings`.
- Use structured JSON only where flexible sections require it.
- Do not use one uncontrolled JSON blob for the entire application.
- Mark missing approved copy as `TODO_CONTENT`.
