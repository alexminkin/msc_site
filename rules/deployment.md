# Deployment Rules

The production architecture must support:

- Next.js application;
- PostgreSQL database;
- S3-compatible Object Storage;
- HTTPS;
- environment-variable and secret management;
- migration step;
- production build;
- domain configuration;
- database backup strategy;
- S3 media backup or retention strategy.

## Provider Rules

The hosting provider is not fixed in the technical specification.

Managed hosting is preferred unless the owner selects a VPS or another target. Docker and Nginx are not mandatory and should be introduced only when the selected hosting environment requires them.

## Launch Steps

1. Provision PostgreSQL.
2. Provision S3-compatible storage.
3. Configure production secrets.
4. Run Prisma migrations.
5. Seed initial content if required.
6. Create the administrator securely.
7. Deploy the Next.js application.
8. Configure domain and HTTPS.
9. Verify backups.
10. Complete the production acceptance checklist.

## Environment Variables

Create `.env.example` with names only. Never commit real values.
