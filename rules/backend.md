# Backend Rules

Backend behavior must live inside Next.js API Routes.

## Stack

- Next.js API Routes under `src/pages/api/`
- TypeScript
- Zod
- Better Auth
- Prisma ORM
- PostgreSQL
- S3-compatible Object Storage

Do not add a separate Express, NestJS, GraphQL, or tRPC backend for the MVP.

## API Rules

Every mutation endpoint must:

1. verify the HTTP method;
2. verify admin authentication when required;
3. validate input with Zod;
4. perform database work through Prisma;
5. perform media work through the server-side S3 client;
6. return typed success/error responses;
7. avoid leaking stack traces or secrets.

## Required API Areas

- Better Auth route: `/api/auth/[...all]`
- Public contact submission: `/api/contact`
- Admin pages, services, team, media, settings, SEO, and contact submissions under `/api/admin/`

## Contact Form

- Validate on client and server.
- Save validated submissions in PostgreSQL.
- Include spam or abuse protection.
- Database-only handling is sufficient for MVP unless integrations are approved later.

## Media

- Store actual files in S3-compatible object storage.
- Store only metadata, references, object keys, URLs, size, dimensions, and alt text in PostgreSQL.
- Validate file type and file size before upload.
