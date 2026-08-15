# Admin Rules

The website must include a private administration interface.

## Routes

- `/admin/login`
- `/admin`
- `/admin/pages`
- `/admin/services`
- `/admin/team`
- `/admin/media`
- `/admin/seo`
- `/admin/settings`
- `/admin/contact-submissions`

## Authentication

- Use Better Auth.
- Do not build public registration.
- Create administrator accounts through a secure setup or deployment process.
- Verify sessions server-side before rendering protected pages.
- Every state-changing admin API route must independently verify authorization.
- Client-side hiding is not security.

## Admin UX

Admin forms must:

- show required fields clearly;
- show field-level validation messages;
- preserve entered data on validation errors;
- show save success and error states;
- confirm destructive actions;
- prevent repeated saves where practical.

## Editing Scope

Admin must manage:

- pages;
- services and service FAQs;
- team members;
- media and alt text;
- SEO metadata;
- site settings;
- social links;
- contact submissions.

MVP role is `ADMIN`. Do not build complex RBAC unless explicitly approved.
