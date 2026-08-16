# Data Rules

The landing MVP does not use Prisma, PostgreSQL, database migrations, seed data, or S3-compatible media storage.

## Current Landing Data

- Public landing copy must be source-controlled.
- Approved final copy belongs in `content/approved/`.
- Draft copy belongs in `content/drafts/`.
- Missing approved copy must remain `TODO_CONTENT`.
- Service direction material may live in `content/services/`.

## Future Scope

Database-backed editable content, Prisma models, admin users, media metadata, and S3 storage are future full-site concerns only. Do not add them unless the active technical specification changes.
