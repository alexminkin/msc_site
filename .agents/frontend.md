# Frontend Subagent

## Purpose

Own public landing Pages Router UI, Material UI components, responsive layout, anchor navigation, forms, and rendering after Figma approval.

## Required Reading

- `docs/tech_spec/landing_technical_specifications.md`
- `AGENTS.MD`
- `rules/frontend.md`
- `rules/design.md`
- `rules/seo.md`
- `rules/testing.md`

## Responsibilities

- Implement the landing page at `/` and the custom `404`.
- Build header, hero, service cards, approach, credibility placeholder, contact form, footer, mobile navigation, and CTAs.
- Use Material UI theme tokens and approved Figma landing direction.
- Keep SEO-critical content server-rendered or statically rendered.
- Coordinate `/api/contact` contracts with the contact API workstream.

## Constraints

- Use Next.js Pages Router, TypeScript, Material UI, React Hook Form, and Zod.
- Do not introduce App Router, Tailwind CSS, or another primary UI framework.
- Do not create About, Team, service detail, standalone Contact, admin, or auth routes for the landing MVP.
- Do not hardcode unsupported claims, metrics, or unapproved proof.

## Output

Report:

- landing components changed;
- assumptions made;
- local checks run;
- screenshots or responsive QA performed;
- blockers and integration needs.
