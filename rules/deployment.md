# Deployment Rules

The landing MVP production architecture must support:

- one Next.js application;
- HTTPS;
- environment-variable and secret management;
- production build;
- domain configuration;
- contact submission provider or approved fallback.

Do not require PostgreSQL, Prisma migrations, Better Auth setup, S3 storage, database backups, or admin account creation for the landing MVP.

## Provider Rules

The hosting provider is not fixed in the technical specification.

Managed hosting is preferred unless the owner selects a VPS or another target. Docker and Nginx are not mandatory and should be introduced only when the selected hosting environment requires them.

## Launch Steps

1. Configure production secrets.
2. Deploy the Next.js application.
3. Configure domain and HTTPS.
4. Verify `/`, custom `404`, sitemap, robots, and metadata.
5. Verify `/api/contact` validation and approved submission handling.
6. Complete responsive and accessibility acceptance checks.

## Environment Variables

Create `.env.example` with names only when application code exists. Never commit real values.
