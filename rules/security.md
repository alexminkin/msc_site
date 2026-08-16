# Security Rules

Security requirements apply to the public landing page, `/api/contact`, and deployment configuration.

## General

- Use HTTPS in production.
- Keep secrets only in environment variables or deployment secret management.
- Never expose privileged secrets in browser bundles.
- Validate submitted data server-side with Zod.
- Use rate limiting or equivalent abuse protection for public contact submissions.
- Return safe error responses.
- Review dependencies before production release.
- Avoid logging sensitive message contents in public or long-lived logs unless explicitly approved.

## Landing Contact API

- Do not expose email provider, webhook, or API secrets to the browser.
- Reject unsupported methods.
- Reject invalid payloads.
- Do not expose stack traces or provider responses.
- Do not commit `.env` files with real values.

## Repository Hygiene

Never commit:

- `.env` with real values;
- contact provider secrets;
- webhook secrets;
- private MCP tokens;
- private SSH keys;
- future database URLs, S3 credentials, Better Auth secrets, or production admin passwords.
