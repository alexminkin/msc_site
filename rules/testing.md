# Testing Rules

Run checks relevant to the landing MVP and fix introduced errors before handoff.

## Required Technical Checks

- `npm install` succeeds.
- lint passes.
- TypeScript check passes.
- production build succeeds.
- no major console errors.
- no broken internal links or anchors.
- no horizontal overflow at required breakpoints.
- `/` renders successfully.
- custom `404` renders successfully.
- `/api/contact` rejects unsupported methods.
- `/api/contact` validates bad payloads.
- `/api/contact` returns safe responses.
- sitemap and robots rules match the landing routes.

Do not run or require Prisma migrations, Prisma seed, admin login checks, protected route checks, or S3 checks for the landing MVP.

## Functional Coverage

Test:

- header navigation;
- anchor links;
- mobile menu;
- CTAs;
- service cards;
- contact form validation, pending, success, and error states;
- custom 404;
- keyboard navigation and focus states.

## Responsive And Accessibility

Test responsive behavior at:

- 320 px
- 375 px
- 768 px
- 1024 px
- 1440 px

Check labels, contrast, semantic structure, reduced-motion behavior where motion exists, and that text and controls do not overlap or clip.
