# Security Rules

Security requirements apply to public APIs, admin pages, authentication, media, and deployment.

## General

- Use HTTPS in production.
- Keep secrets only in environment variables or deployment secret management.
- Never expose privileged secrets in browser bundles.
- Validate submitted data server-side with Zod.
- Use rate limiting or equivalent abuse protection for login and public submission endpoints.
- Return safe error responses.
- Review dependencies before production release.
- Do not expose PostgreSQL directly to the browser.

## Admin

- Verify Better Auth sessions server-side.
- Exclude admin routes from sitemap.
- Add `noindex, nofollow` to admin pages.
- Require authorization for every protected mutation.
- Avoid logging passwords, session tokens, or secrets.
- Sanitize rich text if rich text editing is implemented.

## Media

- Keep S3 credentials server-only.
- Use server-mediated uploads or short-lived presigned URLs generated only after admin authorization.
- Validate file type and size.
- Prevent executable uploads.
- Treat SVG uploads carefully and intentionally.

## Repository Hygiene

Never commit:

- `.env` with real values;
- database URLs;
- S3 credentials;
- Better Auth secrets;
- production admin passwords;
- private MCP tokens;
- private SSH keys.
