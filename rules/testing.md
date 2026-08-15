# Testing Rules

Run checks relevant to each feature and fix introduced errors before handoff.

## Required Technical Checks

- `npm install` succeeds.
- lint passes.
- TypeScript check passes.
- production build succeeds.
- Prisma migrations apply successfully.
- Prisma seed works on a clean database.
- no major console errors.
- no broken internal links.
- sitemap excludes admin routes.
- robots rules are correct.
- protected API endpoints reject unauthorized requests.
- admin content changes appear correctly on public pages.

## Functional Coverage

Test:

- public routes;
- navigation;
- services dropdown;
- mobile menu;
- CTAs;
- LinkedIn and Instagram links;
- contact form validation, success, and error states;
- custom 404;
- admin login/logout;
- unauthorized redirect;
- page, service, team, settings, SEO, and media editing;
- contact submission viewing;
- destructive-action confirmation.

## Responsive And Accessibility

Test responsive behavior at:

- 320 px
- 375 px
- 768 px
- 1024 px
- 1440 px

Check keyboard navigation, focus states, labels, contrast, dialogs, menus, and semantic structure.
