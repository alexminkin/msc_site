# Backend Rules

Backend behavior for the landing MVP must live inside Next.js API Routes.

## Stack

- Next.js API Routes under `src/pages/api/`
- TypeScript
- Zod

Do not add Better Auth, Prisma, PostgreSQL, S3-compatible storage, Express, NestJS, GraphQL, or tRPC for the landing MVP.

## API Rules

Every mutation endpoint must:

1. verify the HTTP method;
2. validate input with Zod;
3. apply spam or abuse protection where relevant;
4. handle approved server-side submission delivery;
5. return typed success/error responses;
6. avoid leaking stack traces, provider details, or secrets.

## Required API Area

- Public contact submission: `/api/contact`

Do not implement `/api/admin/*` or `/api/auth/*` routes for the landing MVP.

## Contact Form

- Validate on client and server.
- Use the landing-spec contact request shape.
- Accepted production handling requires an approved email provider, webhook, or other approved integration.
- A secure deployment-side log is allowed only as a temporary development fallback.
- Do not commit provider credentials.
