# MinkinSpace Consulting - Landing Website Technical Specification

## 1. Document Information

- Project: MinkinSpace Consulting Landing Website
- Document type: Technical Specification
- Status: Draft baseline for landing-version implementation
- Version: 1.0
- Owner: MinkinSpace Consulting
- Primary implementation tool: Codex / AI coding agent
- Last updated: 2026-08-16
- Replaces for this version: full corporate website scope with admin panel
- Does not replace permanently: `docs/tech_spec/technical_specifications.md`

## 2. Project Goal

Build a modern, lightweight landing website for MinkinSpace Consulting.

The landing version must:

- explain what MinkinSpace Consulting does;
- communicate expertise in AI, automation, IT, analytics, marketing, and AI Search / GEO;
- show the main service directions on one public page;
- generate consultation requests through a validated contact form;
- provide strong SEO and AI Search / GEO foundations;
- work well on desktop, tablet, and mobile;
- remain simple to deploy and maintain without an admin panel.

This version is intentionally not a full multi-page corporate website. It is a focused public landing page with a contact workflow.

## 3. Scope

### 3.1 In Scope

- One public landing page at `/`.
- Custom `404` page.
- Server-validated contact form.
- Basic public API endpoint for contact submission.
- Static or source-controlled content.
- SEO metadata, Open Graph metadata, sitemap, robots.txt, favicon, and structured data where appropriate.
- Responsive implementation for `320`, `375`, `768`, `1024`, and `1440` px.
- Figma-approved landing layout implementation after explicit owner approval.

### 3.2 Out Of Scope For Landing Version

- Admin panel.
- Admin login.
- Better Auth.
- Admin API routes.
- Admin content editing.
- PostgreSQL content management.
- Prisma schema and migrations.
- S3-compatible media upload management.
- Media library.
- Separate service detail pages.
- Team page.
- About page.
- Blog, insights, cases, industries, pricing pages, and legal pages unless explicitly added later.
- External CMS.

If these features become required later, update this specification before implementation.

## 4. Fixed Technology Stack

Use:

```text
Next.js
Pages Router
TypeScript
Material UI
React Hook Form
Zod
Next.js API Routes
npm
```

Do not introduce:

- App Router;
- Tailwind CSS;
- Redux;
- NestJS;
- Express as a separate server;
- GraphQL;
- tRPC;
- Redis;
- microservices;
- Kubernetes;
- external CMS;
- multiple primary UI libraries.

### 4.1 Removed From Landing Version

The following technologies from the full corporate-site baseline are not required for this landing version:

- Better Auth;
- Prisma ORM;
- PostgreSQL;
- S3-compatible Object Storage.

They should not be installed or configured unless the landing scope changes.

## 5. High-Level Architecture

```text
Browser
   |
   v
Next.js Pages Router Application
   |
   |-- Public landing page (`pages/index.tsx`)
   |
   |-- Public API (`pages/api/contact.ts`)
          |
          +--> Zod validation
          +--> Safe server-side handling
```

### 5.1 Architecture Principles

- One repository.
- One Next.js application.
- Pages Router only.
- One primary UI system: Material UI.
- Public content is rendered server-side or statically at build time.
- No business-critical secrets in browser code.
- No database dependency for landing-version launch.
- No admin-only code paths.
- Contact submissions must be handled server-side and protected against abuse.

## 6. Routes

### 6.1 Public Routes

```text
/
/404
```

### 6.2 API Routes

```text
/api/contact
```

### 6.3 Forbidden Routes For Landing Version

The landing version must not implement:

```text
/admin
/admin/login
/api/admin/*
/api/auth/*
/services/*
/about
/team
/contact
```

If visitors request non-existent routes, serve the custom `404`.

## 7. Landing Page Content Structure

The landing page should follow the approved Figma landing design direction.

Current Figma references:

- Editable file: `https://www.figma.com/design/9ZXhf3VkhxszM2P98ZDUVp`
- Desktop landing frame: `Main page_v2 / Dark Space 1440` (`39:2`)
- Tablet landing frame: `Main page_v2 / Dark Space Tablet 768` (`40:2`)
- Mobile landing frame: `Main page_v2 / Dark Space Mobile 375` (`40:127`)
- Small mobile landing frame: `Main page_v2 / Dark Space Mobile 320` (`40:248`)

The previous `Main page_v1` frames are retained only as historical references.

### 7.1 Required Sections

1. Header
2. Hero
3. Service overview / capability cards
4. Process or approach section
5. Credibility or proof placeholder section
6. Contact / consultation request section
7. Footer

### 7.2 Header

Required elements:

- MinkinSpace Consulting logo or wordmark;
- anchor navigation to landing sections;
- primary CTA to contact section;
- responsive mobile navigation if the desktop nav does not fit.

Suggested anchor IDs:

```text
#services
#approach
#contact
```

### 7.3 Hero

Must communicate:

- company name;
- practical consulting focus;
- AI, automation, IT, analytics, marketing, and AI Search / GEO service areas;
- clear primary CTA.

Do not invent performance claims, client logos, statistics, testimonials, or guarantees.

### 7.4 Services

Show the six service directions as landing-page cards:

- Business Process Automation;
- AI Pre-Sales;
- IT Infrastructure Audit;
- Marketing AI Analysis;
- AI Search / GEO;
- Social Marketing.

Each card should include:

- service name;
- short approved or `TODO_CONTENT` description;
- business problem or intended value, only if approved.

No service detail routes are required in this version.

### 7.5 Approach

Show a simple process such as:

- Discover;
- Prioritize;
- Implement;
- Measure.

The process must avoid unsupported promises. It can describe the working method, not guaranteed outcomes.

### 7.6 Credibility / Proof

Include a section reserved for approved credibility signals.

Until approved source material exists, use `TODO_CONTENT` and do not invent:

- case results;
- client names;
- testimonials;
- certifications;
- years of experience;
- numerical impact metrics.

### 7.7 Contact Section

The contact section must include a consultation request form.

Required fields:

- name;
- email;
- company or organization, optional;
- service interest, optional;
- message or project context.

Optional fields:

- phone;
- preferred contact method;
- consent checkbox if required by final legal/privacy requirements.

## 8. Content Rules

- Approved copy should live in `content/approved/` before being treated as final implementation copy.
- Draft copy may live in `content/drafts/`.
- Missing approved content must remain visible as `TODO_CONTENT`.
- Do not copy third-party text, images, screenshots, proprietary assets, or layouts directly.
- Do not make unsupported business claims.
- Do not guarantee rankings, AI-answer inclusion, revenue growth, cost savings, or delivery outcomes.

## 9. Design And UI Requirements

### 9.1 Visual Direction

Use the approved landing Figma direction:

- dark space consulting/SaaS palette;
- clean professional layout;
- original luminous node-and-edge graph background visible across the page while scrolling;
- restrained technical depth, with enough graph density to be visible without overloading content;
- UsedeskAI-inspired landing rhythm only as a competitor benchmark, without copying text, layout, images, metrics, or proprietary assets;
- Forward Orbit logo concept where logo work is included.

Avoid:

- generic robot imagery;
- AI brain icons;
- literal gears;
- overloaded gradients;
- one-note decorative space effects that reduce readability;
- fake metrics;
- dense dashboards that distract from the landing CTA.

### 9.2 Material UI

- Use Material UI as the primary component system.
- Centralize theme configuration for palette, typography, spacing, breakpoints, shape, shadows, and component overrides.
- Use MUI components for buttons, forms, menus, layout primitives, and feedback states when appropriate.
- Keep custom styling compatible with the centralized MUI theme.

### 9.3 Responsiveness

Implement and verify at:

```text
320 px
375 px
768 px
1024 px
1440 px
```

Mobile requirements:

- no horizontal overflow;
- readable headings and body text;
- tappable CTAs;
- form fields usable on small screens;
- stacked service cards;
- navigation accessible without hover.

### 9.4 Accessibility

Target WCAG 2.2 AA where reasonably achievable:

- semantic landmarks;
- one H1;
- logical H2/H3 structure;
- visible focus states;
- keyboard-accessible navigation and form controls;
- labeled inputs;
- sufficient color contrast;
- accessible button and link names;
- no hover-only interactions;
- reduced-motion support if animation is used.

## 10. Frontend Implementation

### 10.1 Project Structure

Recommended source structure:

```text
src/
  pages/
    _app.tsx
    _document.tsx
    index.tsx
    404.tsx
    api/
      contact.ts
  components/
    landing/
      LandingHeader.tsx
      HeroSection.tsx
      ServicesSection.tsx
      ApproachSection.tsx
      CredibilitySection.tsx
      ContactSection.tsx
      LandingFooter.tsx
    forms/
      ContactForm.tsx
  lib/
    validation/
      contact.ts
    contact/
      submitContact.ts
    seo/
      metadata.ts
  theme/
    index.ts
```

Exact file names may be adjusted during implementation, but admin-specific directories should not be created.

### 10.2 Rendering

The landing page may use static generation or server-side rendering.

Preferred:

- static render for source-controlled content;
- client interactivity only for navigation, form state, and progressive enhancements.

Do not rely on client-side fetching for:

- document title;
- meta description;
- H1;
- primary service descriptions;
- core CTA copy.

### 10.3 Forms

- Use React Hook Form for form state.
- Use Zod for validation schema.
- Reuse the same Zod schema on client and server.
- Show clear success, validation error, and generic failure states.
- Prevent duplicate submission while a request is pending.

## 11. Contact API

### 11.1 Endpoint

```text
POST /api/contact
```

### 11.2 Request Body

```ts
type ContactRequest = {
  name: string;
  email: string;
  company?: string;
  serviceInterest?: string;
  message: string;
  phone?: string;
  preferredContactMethod?: "email" | "phone";
};
```

Final field names should match the implemented Zod schema.

### 11.3 Validation

Server-side validation must enforce:

- required name;
- valid email;
- required message;
- maximum lengths for all string fields;
- allowed enum values for service interest and preferred contact method, if enums are used;
- rejection of unsupported HTTP methods.

### 11.4 Submission Handling

For landing-version MVP, accepted handling options are:

- send an email through an approved transactional email provider;
- forward to an approved webhook;
- log to a secure deployment-side destination only as a temporary development fallback.

The production approach must be approved before launch. Do not commit provider credentials.

### 11.5 API Response

Success:

```ts
type ContactSuccessResponse = {
  ok: true;
};
```

Error:

```ts
type ContactErrorResponse = {
  ok: false;
  error: "VALIDATION_ERROR" | "METHOD_NOT_ALLOWED" | "RATE_LIMITED" | "SUBMISSION_FAILED";
};
```

Do not expose stack traces or secret provider details.

## 12. Security Requirements

- Use HTTPS in production.
- Keep all secrets in environment variables or deployment secret management.
- Do not expose email provider, webhook, or API secrets to the browser.
- Validate all contact submissions server-side with Zod.
- Add spam and abuse protection to `/api/contact`.
- Rate-limit or otherwise throttle repeated submissions.
- Return safe generic errors.
- Avoid logging sensitive user messages in public or long-lived logs unless explicitly approved.
- Do not commit `.env` files with real values.

## 13. SEO And GEO Requirements

### 13.1 Required SEO

The landing page must include:

- unique `<title>`;
- unique meta description;
- canonical URL;
- Open Graph title, description, and image;
- one H1;
- semantic H2/H3 hierarchy;
- favicon;
- robots.txt;
- XML sitemap;
- accessible internal anchor links.

### 13.2 Structured Data

Evaluate and implement where matching visible content exists:

- `Organization`;
- `ProfessionalService`;
- `Service`;
- `Person`, only if approved founder/team content is visible;
- `FAQPage`, only if visible FAQ content exists.

Structured data must match visible page content.

### 13.3 GEO Requirements

Make these entities explicit and easy to identify:

- MinkinSpace Consulting;
- AI consulting;
- business process automation;
- AI pre-sales systems;
- IT infrastructure audit;
- marketing AI analysis;
- AI Search / GEO;
- social marketing;
- contact path.

## 14. Analytics And Monitoring

Analytics is optional for landing MVP.

If analytics is added:

- use a privacy-conscious provider where possible;
- do not add tracking that conflicts with legal/privacy requirements;
- document the provider and environment variables;
- verify that contact form events do not include sensitive message contents.

Error monitoring is optional but recommended before paid traffic or public launch.

## 15. Environment Variables

Potential environment variables:

```text
NEXT_PUBLIC_SITE_URL
CONTACT_SUBMISSION_PROVIDER
CONTACT_EMAIL_TO
CONTACT_EMAIL_FROM
CONTACT_EMAIL_API_KEY
CONTACT_WEBHOOK_URL
CONTACT_WEBHOOK_SECRET
RATE_LIMIT_SECRET
```

Only variables prefixed with `NEXT_PUBLIC_` may be exposed to browser code.

Do not define unused production secrets.

## 16. Testing And Acceptance Criteria

### 16.1 Technical Checks

Before handoff:

- `npm install` succeeds;
- lint passes;
- TypeScript check passes;
- production build succeeds;
- no major browser console errors;
- no horizontal overflow at required breakpoints;
- `/` renders successfully;
- custom `404` renders successfully;
- `/api/contact` rejects unsupported methods;
- `/api/contact` validates bad payloads;
- `/api/contact` returns safe responses.

### 16.2 Functional Checks

Test:

- header navigation;
- anchor links;
- primary CTA scroll or navigation to contact section;
- service cards;
- contact form validation;
- contact form success state;
- contact form failure state;
- keyboard navigation;
- focus states.

### 16.3 SEO Checks

Verify:

- title and meta description;
- canonical URL;
- Open Graph metadata;
- robots.txt;
- sitemap.xml;
- one H1;
- structured data validity where implemented;
- no admin routes in sitemap because admin routes do not exist.

### 16.4 Responsive Checks

Verify at:

```text
320 px
375 px
768 px
1024 px
1440 px
```

Acceptance requires no overlapping text, no clipped CTA labels, and no unusable form controls.

## 17. Deployment Requirements

- Deploy as a single Next.js application.
- Use HTTPS.
- Configure production domain through `NEXT_PUBLIC_SITE_URL`.
- Configure contact submission secrets in deployment secret storage.
- Do not expose private environment variables in the client bundle.
- Verify production build and contact flow in the deployed environment.

## 18. Migration Path To Full Corporate Website

If the project later returns to the full corporate-site scope:

- re-open `docs/tech_spec/technical_specifications.md` as the baseline;
- add admin pages only after explicit owner approval;
- reintroduce Better Auth, Prisma, PostgreSQL, and S3 only when admin/content management is required;
- add multi-page routes incrementally;
- migrate source-controlled landing content into database-backed editable content only after data models are approved.

## 19. Open Decisions

- Final approved landing page copy.
- Final primary CTA wording.
- Final public contact email or recipient.
- Contact submission provider: email, webhook, or another approved integration.
- Whether phone field is required, optional, or omitted.
- Whether legal/privacy text must be visible near the form.
- Final production domain.
- Analytics provider, if any.
- Open Graph image source.
