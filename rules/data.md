# Data Rules

The landing MVP does not use Prisma, PostgreSQL, database migrations, seed data, or S3-compatible media storage.

## Current Landing Data

- Public landing copy must be source-controlled.
- Approved final copy belongs in `content/approved/`.
- Draft copy belongs in `content/drafts/`.
- Missing approved copy must remain `TODO_CONTENT`.
- The main website service text source is `content/services/services_description_en.md`.
- Use `content/services/services_description_en.md` for service names, descriptions, value statements, scenario copy, and service CTAs unless the owner explicitly replaces it.
- Other service files in `content/services/` are supporting references and must not override `content/services/services_description_en.md` for public website service copy.

## Future Scope

Database-backed editable content, Prisma models, admin users, media metadata, and S3 storage are future full-site concerns only. Do not add them unless the active technical specification changes.
