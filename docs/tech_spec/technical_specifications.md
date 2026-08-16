# MinkinSpace Consulting — Corporate Website Technical Specification

> Status note, 2026-08-16: this document is not the active source of truth for the current landing MVP. Use `docs/tech_spec/landing_technical_specifications.md` for current implementation decisions. This full corporate website specification is retained only as future scope until the owner explicitly reactivates it.

## 1. Document Information

- Project: MinkinSpace Consulting Corporate Website
- Document type: Technical Specification
- Status: Future full corporate website reference, inactive for current landing MVP
- Version: 1.0
- Owner: MinkinSpace Consulting
- Primary implementation tool: Codex / AI coding agent
- Last updated: 2026-08-16

---

## 2. Project Goal

Develop a modern, lightweight and maintainable corporate website for MinkinSpace Consulting.

The website must:

- clearly explain the company and its services;
- communicate expertise in AI, automation, IT, analytics and marketing;
- generate consultation and project requests;
- provide strong SEO and AI Search / GEO foundations;
- work well on desktop, tablet and mobile;
- allow routine content editing through a secure internal admin panel;
- remain technically simple enough to maintain without a large engineering team.

The project must be implemented as a single Next.js application. A separate frontend, backend or external CMS is not required for the MVP.

---

## 3. Fixed Technology Stack

The following technology stack is approved and must be treated as a project constraint.

```text
Next.js
Pages Router
TypeScript
Material UI
React Hook Form
Zod
Next.js API Routes
Better Auth
Prisma ORM
PostgreSQL
S3-compatible Object Storage
npm
```

### 3.1 Stack Responsibilities

| Layer | Technology | Responsibility |
|---|---|---|
| Application framework | Next.js | Public website, admin interface, server rendering and backend endpoints |
| Routing | Pages Router | All public, admin and API routing under `pages/` |
| Language | TypeScript | Application code and shared types |
| UI system | Material UI | Components, responsive UI, theme and design tokens |
| Forms | React Hook Form | Form state and user interaction |
| Validation | Zod | Shared validation schemas for forms and APIs |
| Backend | Next.js API Routes | Admin mutations, authentication integration, forms and media endpoints |
| Authentication | Better Auth | Secure administrator authentication and session management |
| ORM | Prisma ORM | Typed database access and migrations |
| Database | PostgreSQL | Website content, settings, admin/auth data, form submissions and media metadata |
| Media storage | S3-compatible Object Storage | Images, logos and uploaded media files |
| Package manager | npm | Dependency and script management |

### 3.2 Explicitly Out of Scope for MVP

Do not introduce the following unless this specification is changed later:

- App Router;
- Tailwind CSS;
- Redux;
- Zustand unless a concrete need appears;
- NestJS;
- Express as a separate server;
- GraphQL;
- tRPC;
- Redis;
- microservices;
- Kubernetes;
- external CMS platforms such as WordPress, Strapi, Directus, Sanity or Contentful;
- multiple UI libraries for the same purpose.

Small implementation packages are allowed when required by the fixed stack, for example S3 SDKs, MUI icon packages or Better Auth adapters. They must not introduce a new architectural layer.

---

## 4. High-Level Architecture

```text
Browser
   |
   v
Next.js Application
   |
   |-- Public Pages (`pages/`)
   |     |
   |     +--> Prisma --> PostgreSQL
   |
   |-- Admin Pages (`pages/admin/`)
   |     |
   |     +--> Better Auth
   |     +--> API Routes
   |              |
   |              +--> Zod validation
   |              +--> Prisma --> PostgreSQL
   |              +--> S3-compatible Object Storage
   |
   +-- Public API / Contact API (`pages/api/`)
          |
          +--> Zod validation
          +--> Prisma --> PostgreSQL
```

### 4.1 Architecture Principles

- One repository.
- One Next.js application.
- One PostgreSQL database.
- One UI component system: Material UI.
- One database access layer: Prisma.
- One authentication system: Better Auth.
- No duplicated business content when it can be stored centrally.
- No business-critical secrets in frontend code.
- Public content should be server-rendered for SEO and simplicity.
- Admin content changes must not require source-code editing.

---

## 5. Public Sitemap

### 5.1 MVP Pages

```text
/
/about
/services
/services/business-process-automation
/services/ai-pre-sales
/services/it-infrastructure-audit
/services/marketing-ai-analysis
/services/ai-search-geo
/services/social-marketing
/ai-for-business
/marketing
/contact
```

### 5.2 Future-Ready Pages

The architecture should allow later implementation of:

```text
/cases
/cases/[slug]
/insights
/insights/[slug]
/industries/[slug]
/team
/privacy-policy
/cookie-policy
/terms
```

These pages are not required for MVP unless added explicitly later.

---

## 6. Admin Sitemap

The website must include a private administration interface.

```text
/admin/login
/admin
/admin/pages
/admin/services
/admin/media
/admin/seo
/admin/settings
/admin/contact-submissions
```

Requirements:

- `/admin` is the protected root of the administration interface.
- Unauthenticated users must be redirected to `/admin/login`.
- Admin pages must not appear in the XML sitemap.
- Admin pages must use `noindex, nofollow`.
- Admin data must not be available through unauthenticated API calls.
- There is no public administrator registration.

---

## 7. Global Public Layout

### 7.1 Header

Required elements:

- MinkinSpace Consulting logo;
- Home;
- About Us;
- AI for Business;
- Marketing;
- Contact;
- primary CTA: `Request a Consultation`;
- responsive mobile navigation.

Behavior:

- visible on all public pages;
- sticky header is preferred;
- accessible by keyboard;
- responsive from 320 px viewport width;
- active page may be visually highlighted.

### 7.2 Footer

Required elements:

- company logo or wordmark;
- short company description;
- public navigation;
- service links;
- contact information;
- social links;
- copyright;
- legal links when legal pages are implemented.

Approved social links:

```text
LinkedIn: https://www.linkedin.com/in/alexminkinspace/
Instagram: https://www.instagram.com/minkinspace
```

Social URLs must be stored in `SiteSettings` and editable from the admin panel. They must not be duplicated as hardcoded constants across individual page components.

External social links should use accessible labels. If opened in a new tab, use `rel="noopener noreferrer"`.

### 7.3 Global CTA

Major public pages must contain at least one conversion block before the footer.

Default CTA intent:

- request a consultation;
- discuss a project;
- contact MinkinSpace Consulting.

---

## 8. Main Page

### 8.1 Goal

Explain what MinkinSpace Consulting does, show the main services, establish credibility and drive consultation requests.

### 8.2 Required Sections

1. Hero
2. Why MinkinSpace Consulting
3. Services overview
4. How We Work
5. Expertise / proof
6. Selected experience or cases
7. Final CTA

### 8.3 Hero

Must contain:

- one H1;
- short value proposition;
- supporting paragraph;
- primary CTA;
- optional secondary CTA;
- minimal technology-oriented visual.

The hero must answer:

- who the company is;
- what business problems it solves;
- what the visitor should do next.

### 8.4 Services Overview

Display six service cards:

1. Business Process Automation
2. AI Pre-Sales
3. IT Infrastructure Audit
4. Marketing AI Analysis
5. AI Search & GEO
6. Social Marketing

Each card must contain:

- service name;
- short business-focused description;
- optional icon;
- link to the service page.

### 8.5 How We Work

Default four-step structure:

1. Business problem discovery
2. Audit and analysis
3. Solution / roadmap / implementation
4. Measurement and optimization

Do not publish unsupported statistics, client claims or guarantees.

---

## 9. About Us Page

### 9.1 Goal

Explain the company positioning, philosophy, expertise and consulting approach.

### 9.2 Recommended Sections

1. Introduction
2. Mission
3. What Makes Us Different
4. Areas of Expertise
5. Selected industries / experience
6. CTA

### 9.3 Areas of Expertise

Potential categories:

- AI and LLM systems;
- business process automation;
- data and analytics;
- IT architecture and infrastructure;
- product and project management;
- marketing analytics;
- AI Search / GEO.

Only publish experience that is accurate and approved.

---

## 10. Services Overview Page

### 10.1 Goal

Help visitors understand all services and identify the most relevant one.

### 10.2 Required Elements

- H1;
- introductory description;
- six service cards;
- optional business-problem-to-service mapping;
- CTA.

Example mapping:

| Business Problem | Relevant Service |
|---|---|
| Too many manual operations | Business Process Automation |
| Sales team spends too much time preparing proposals | AI Pre-Sales |
| IT systems are fragmented or unreliable | IT Infrastructure Audit |
| Marketing decisions are based on incomplete data | Marketing AI Analysis |
| Brand is poorly represented in AI answers | AI Search & GEO |
| Social channels lack a measurable growth system | Social Marketing |

---

## 11. Reusable Service Page Template

All six service pages must use one reusable page structure while receiving content from PostgreSQL.

Required sections:

1. Hero
2. Business Problem
3. What We Do
4. Deliverables
5. Process
6. Expected Business Effect
7. Tools / Technologies
8. Relevant Experience / Case
9. FAQ
10. CTA

Requirements:

- service-specific title and metadata;
- one H1;
- business value explained before technical implementation details;
- no unsupported guarantees;
- content editable from `/admin/services`;
- service order editable in admin;
- service publication status supported.

---

## 12. Service Content Requirements

### 12.1 Business Process Automation

Topics:

- process audit;
- bottleneck identification;
- workflow automation;
- AI agents;
- CRM / ERP / task-management integrations;
- document automation;
- notifications and reporting;
- data synchronization;
- human-in-the-loop workflows.

Potential deliverables:

- current-state process map;
- target-state process map;
- automation roadmap;
- prioritized backlog;
- prototype or MVP;
- integrations;
- documentation;
- KPI framework.

### 12.2 AI Pre-Sales

Topics:

- lead enrichment;
- lead qualification;
- automated company research;
- personalized outreach preparation;
- proposal draft generation;
- CRM enrichment;
- meeting preparation;
- call summaries;
- knowledge-base-assisted sales agents.

Potential deliverables:

- pre-sales audit;
- AI assistant / agent prototype;
- CRM integration;
- lead-scoring logic;
- prompt / knowledge architecture;
- workflows;
- sales-team usage guidelines.

### 12.3 IT Infrastructure Audit

Topics:

- architecture review;
- systems inventory;
- integration map;
- data-flow review;
- CRM / ERP / databases;
- cloud / hosting / deployment;
- monitoring;
- access management;
- technical debt;
- scalability and reliability risks;
- AI readiness.

Potential deliverables:

- infrastructure map;
- risks register;
- technical debt list;
- priority matrix;
- architecture recommendations;
- modernization roadmap.

### 12.4 Marketing AI Analysis

Topics:

- marketing data audit;
- funnel analysis;
- campaign analysis;
- customer segmentation;
- competitor analysis;
- dashboards;
- AI-assisted research;
- hypothesis generation;
- forecasting where justified.

Potential deliverables:

- marketing audit;
- KPI framework;
- dashboard / report;
- channel analysis;
- customer segments;
- competitor report;
- prioritized growth hypotheses;
- recommendations.

### 12.5 AI Search & GEO

GEO means Generative Engine Optimization.

Topics:

- AI search visibility audit;
- brand/entity consistency;
- semantic content structure;
- FAQ and expert content;
- structured data;
- crawlability;
- authority signals;
- content gaps;
- monitoring AI-generated answers;
- alignment with traditional SEO.

Potential deliverables:

- GEO audit;
- AI visibility baseline;
- content/entity map;
- technical recommendations;
- structured content templates;
- priority roadmap;
- monitoring framework.

Do not guarantee ranking or inclusion in AI-generated answers.

### 12.6 Social Marketing

Topics:

- channel strategy;
- audience research;
- content pillars;
- editorial planning;
- content production workflow;
- AI-assisted content operations;
- distribution;
- community management;
- analytics;
- testing and optimization.

Potential deliverables:

- social media audit;
- channel strategy;
- content matrix;
- monthly content plan;
- production workflow;
- reporting dashboard;
- growth hypotheses.

---

## 13. Team Page — Future Version

### 13.1 Goal

Build credibility and show the people behind MinkinSpace Consulting in a later website version. The current public navigation must not include `Team`.

### 13.2 Team Member Fields

- photo;
- full name;
- role;
- short bio;
- expertise;
- LinkedIn or professional profile URL;
- display order;
- publication status.

When implemented, team data must be stored in PostgreSQL and editable from `/admin/team`.

---

## 14. Contact Page

### 14.1 Required Content

- H1;
- short invitation to contact;
- contact form;
- public email;
- optional public phone / messenger;
- LinkedIn;
- Instagram.

### 14.2 Contact Form Fields

- Name — required
- Company — optional
- Work email — required
- Phone / messenger — optional
- Service of interest — optional
- Project description — required
- Consent checkbox — required when legally necessary

### 14.3 Contact Form Processing

Implementation flow:

```text
Contact form
   |
React Hook Form
   |
Zod client validation
   |
POST /api/contact
   |
Zod server validation
   |
Prisma
   |
PostgreSQL ContactSubmission
```

Requirements:

- client-side validation;
- server-side validation;
- spam / abuse protection;
- clear success state;
- clear error state;
- duplicate-submission protection where practical;
- no secrets in client code.

For MVP, saving validated submissions in PostgreSQL is sufficient. Email, CRM, Telegram or webhook notifications may be added later as integrations without changing the core architecture.

---

## 15. Admin Panel

### 15.1 Goal

Allow authorized administrators to manage routine website content without editing code.

### 15.2 Authentication

Use Better Auth.

Requirements:

- no public registration;
- administrator account created through a secure setup/deployment process;
- secure server-side session validation;
- secure cookie configuration in production;
- logout;
- session expiration;
- login abuse protection;
- authentication secrets stored only in environment variables;
- authentication errors must not unnecessarily reveal whether an account exists.

MVP role:

```text
ADMIN
```

Do not build complex RBAC for MVP. Data structures should remain extensible for future roles such as Editor or SEO Manager.

### 15.3 Route Protection

All protected admin pages must verify the session server-side before rendering protected content.

Pages Router implementation may use server-side guards in `getServerSideProps` or an equivalent reusable authentication helper.

Client-side hiding of admin UI is not sufficient security.

Every state-changing API route must independently verify administrator authorization.

### 15.4 Dashboard

Recommended dashboard shortcuts:

- Edit Main Page
- Edit About Us
- Manage Services
- Manage Media
- Manage SEO
- Edit Site Settings
- View Contact Submissions
- Preview Website
- Logout

### 15.5 Page Editing

Admin must be able to edit Main Page, About Us, and Contact content, including:

- page title;
- hero title;
- hero description;
- section titles;
- text blocks;
- CTA labels and URLs;
- related images;
- SEO title;
- meta description;
- Open Graph image;
- publication status where relevant.

### 15.6 Service Editing

Admin must be able to:

- create services;
- edit services;
- reorder services;
- publish/unpublish services;
- edit short card descriptions;
- edit service-page content;
- edit FAQ items;
- edit SEO metadata;
- assign media.

The six MVP services must exist as initial database seed data.

### 15.7 Team Editing — Future Version

When the Team page is added in a later website version, admin should be able to:

- add team members;
- edit team members;
- reorder team members;
- publish/unpublish team members;
- upload/replace photos;
- edit professional links.

### 15.8 Settings Editing

Admin must be able to edit:

- company name;
- public email;
- public phone / messenger if enabled;
- LinkedIn URL;
- Instagram URL;
- footer description;
- primary CTA label;
- primary CTA URL;
- logo references;
- default SEO settings.

---

## 16. Media Management

### 16.1 Storage Architecture

Actual files must be stored in S3-compatible Object Storage.

PostgreSQL stores only metadata and references.

```text
Admin upload
   |
API Route
   |
validation
   |
S3-compatible Object Storage <-- actual file
   |
Prisma --> PostgreSQL <-- metadata / object key / URL / alt text
```

### 16.2 Media Requirements

Admin media interface must support:

- image upload;
- file type validation;
- file size validation;
- safe generated storage keys;
- alt text;
- preview;
- reuse of existing media;
- deletion with reference warning;
- prevention of executable uploads.

Recommended allowed image types for MVP:

- JPEG;
- PNG;
- WebP;
- SVG only when handled safely and intentionally, especially for logo assets.

### 16.3 Media Database Fields

```text
id
objectKey
url
filename
mimeType
size
width
height
altText
createdAt
updatedAt
```

Do not store binary image data directly in PostgreSQL.

---

## 17. Data Model

Use Prisma schema as the source of truth for relational data models and migrations.

### 17.1 Core Entities

Required logical entities:

```text
User / Better Auth entities
Page
Service
ServiceFaq
Media
SiteSettings
ContactSubmission
```

### 17.2 Page

Suggested fields:

```text
id
slug
title
heroTitle
heroDescription
content
seoTitle
seoDescription
ogImageId
publicationStatus
createdAt
updatedAt
```

`content` may use structured JSON where flexible sections are required. Fixed high-value fields should remain explicit columns when practical.

### 17.3 Service

Suggested fields:

```text
id
name
slug
shortDescription
heroTitle
heroDescription
businessProblem
workScope
deliverables
processSteps
expectedEffects
technologies
relevantExperience
seoTitle
seoDescription
ogImageId
sortOrder
publicationStatus
createdAt
updatedAt
```

Arrays / flexible section data may use PostgreSQL JSON where appropriate, but avoid using one uncontrolled JSON blob for the entire application.

### 17.4 ServiceFaq

```text
id
serviceId
question
answer
sortOrder
createdAt
updatedAt
```

### 17.5 TeamMember — Future Version

```text
id
name
role
shortBio
expertise
photoId
linkedinUrl
sortOrder
publicationStatus
createdAt
updatedAt
```

Reserved for the later website version that restores the public Team page.

### 17.6 SiteSettings

Single logical settings record or equivalent key-value structure.

Required values:

```text
companyName
footerDescription
primaryCtaLabel
primaryCtaUrl
contactEmail
contactPhone
linkedinUrl
instagramUrl
logoPrimaryId
logoMarkId
defaultSeoTitle
defaultSeoDescription
defaultOgImageId
```

Initial social values:

```text
linkedinUrl = https://www.linkedin.com/in/alexminkinspace/
instagramUrl = https://www.instagram.com/minkinspace
```

### 17.7 ContactSubmission

```text
id
name
company
email
phone
serviceId
projectDescription
consent
status
createdAt
```

Possible status values:

```text
NEW
READ
ARCHIVED
```

### 17.8 Audit Fields

All editable core entities should include at minimum:

```text
createdAt
updatedAt
```

Where practical, include `updatedByUserId` for administrative changes.

A full revision/history system is not required for MVP.

---

## 18. Public Rendering Strategy

Public content stored in PostgreSQL should be rendered server-side using Pages Router server-side data fetching.

Preferred simple MVP approach:

```text
getServerSideProps
    |
Prisma
    |
PostgreSQL
```

Reasons:

- content is always current after an admin save;
- no additional cache invalidation architecture is required;
- SEO content is delivered in rendered HTML;
- implementation remains straightforward.

Do not fetch critical SEO content only after client-side hydration.

If performance requirements later justify caching or ISR, it may be added as an optimization without changing the core content model.

---

## 19. API Architecture

All API endpoints must live under `pages/api/`.

Suggested structure:

```text
pages/api/
├── auth/
│   └── [...all].ts
├── contact.ts
├── admin/
│   ├── pages/
│   ├── services/
│   ├── media/
│   ├── settings/
│   ├── seo/
│   └── contact-submissions/
```

Exact REST naming may be adjusted during implementation.

### 19.1 API Rules

Every mutation endpoint must:

1. verify HTTP method;
2. verify admin authentication where required;
3. validate input with Zod;
4. perform operation through Prisma or S3 client;
5. return a typed success/error response;
6. avoid leaking stack traces or secrets to clients.

Do not access PostgreSQL directly outside Prisma except for a documented exceptional reason.

---

## 20. Forms and Validation

### 20.1 Standard

Use:

```text
React Hook Form + Zod
```

for public and admin forms.

### 20.2 Validation Rule

Client-side validation improves UX but is never authoritative.

The API must validate all submitted data again with Zod.

Where practical, share schemas between frontend forms and backend routes.

### 20.3 Admin UX

Admin forms must:

- clearly show required fields;
- show field-level validation messages;
- preserve entered data when validation fails;
- show save success/error states;
- confirm destructive actions;
- prevent accidental repeated save actions where practical.

---

## 21. Material UI Requirements

Material UI is the only primary UI component library.

Use MUI for:

- layout primitives where appropriate;
- buttons;
- inputs;
- selects;
- dialogs;
- drawers;
- menus;
- accordions;
- cards;
- tables;
- snackbars;
- admin navigation;
- responsive breakpoints;
- theme tokens.

### 21.1 Styling Strategy

Primary styling should use:

- MUI Theme;
- `sx` prop;
- MUI styled utilities where reusable styled components are justified.

Do not add Tailwind.

Do not add another general-purpose component framework.

### 21.2 Theme

Create centralized theme configuration for:

```text
palette
typography
spacing
breakpoints
shape / border radius
shadows
component overrides
```

Avoid scattering arbitrary colors, font sizes and spacing values throughout components.

---

## 22. Branding and Logo

### 22.1 Design Direction

The visual identity should communicate:

- innovation;
- clarity;
- technology;
- business competence;
- improvement;
- forward movement.

Avoid:

- generic robot imagery;
- AI brain icons;
- literal gears;
- overloaded gradients;
- visually dense dashboards on the public site;
- excessive futuristic effects.

### 22.2 Logo Concept — MinkinSpace Forward Orbit

Recommended main concept:

- clean geometric letter `M`;
- one subtle ascending/orbital trajectory integrated into the symbol;
- trajectory moves upward/forward;
- optional small endpoint representing a target, data point or exploration destination;
- abstract rather than literal space imagery.

Meaning:

```text
M = MinkinSpace
ascending path = improvement and growth
orbit = technology, exploration and systems thinking
minimal geometry = clarity and consulting professionalism
```

### 22.3 Logo Variants

Required final brand assets:

1. Horizontal logo: mark + `MinkinSpace Consulting`
2. Compact mark
3. Monochrome version
4. Light-background version
5. Dark-background version
6. Favicon based on compact mark

Primary vector format: SVG.

The logo must remain readable at small sizes.

---

## 23. Recommended Project Structure

```text
/
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   └── seed.ts
│
├── public/
│   ├── icons/
│   └── static/
│
├── src/
│   ├── pages/
│   │   ├── _app.tsx
│   │   ├── _document.tsx
│   │   ├── index.tsx
│   │   ├── about.tsx
│   │   ├── ai-for-business.tsx
│   │   ├── marketing.tsx
│   │   ├── contact.tsx
│   │   ├── services/
│   │   │   ├── index.tsx
│   │   │   └── [slug].tsx
│   │   ├── admin/
│   │   │   ├── login.tsx
│   │   │   ├── index.tsx
│   │   │   ├── pages.tsx
│   │   │   ├── services.tsx
│   │   │   ├── media.tsx
│   │   │   ├── seo.tsx
│   │   │   ├── settings.tsx
│   │   │   └── contact-submissions.tsx
│   │   └── api/
│   │       ├── auth/
│   │       ├── contact.ts
│   │       └── admin/
│   │
│   ├── components/
│   │   ├── layout/
│   │   ├── navigation/
│   │   ├── sections/
│   │   ├── services/
│   │   ├── forms/
│   │   ├── admin/
│   │   └── ui/
│   │
│   ├── lib/
│   │   ├── auth/
│   │   ├── db/
│   │   ├── storage/
│   │   ├── validation/
│   │   └── seo/
│   │
│   ├── schemas/
│   ├── theme/
│   ├── types/
│   └── config/
│
├── tests/
├── docs/
├── .env.example
├── next.config.js
├── package.json
├── tsconfig.json
└── README.md
```

The exact structure may be refined during implementation, but the project must continue using Pages Router and the approved stack.

---

## 24. Reusable Component Inventory

### Public Layout

- Header
- Footer
- Container
- Section
- PageHero
- CTASection
- Breadcrumbs

### Navigation

- DesktopNav
- ServicesMenu
- MobileNav

### Content

- ServiceCard
- ServiceGrid
- FeatureCard
- ProcessSteps
- StatsBlock
- CaseCard
- FAQAccordion
- RichTextSection

### Forms

- ContactForm
- FormField wrappers where useful
- FormMessage

### Admin

- AdminLayout
- AdminNavigation
- LoginForm
- AdminDashboard
- PageEditorForm
- ServiceEditorForm
- SiteSettingsForm
- SEOEditorForm
- MediaUploader
- MediaLibrary
- ConfirmDialog
- SaveStatus

Use MUI primitives rather than creating unnecessary wrappers around every MUI component.

---

## 25. SEO Requirements

Every indexable public page must support:

- unique `<title>`;
- unique meta description;
- one primary H1;
- logical H2/H3 hierarchy;
- canonical URL;
- Open Graph metadata;
- semantic HTML;
- internal linking;
- XML sitemap;
- robots.txt;
- favicon.

### 25.1 Structured Data

Evaluate and implement where appropriate:

- Organization;
- ProfessionalService;
- Service;
- Person;
- BreadcrumbList;
- FAQPage only when justified by actual visible content and current search requirements.

Structured data must match visible page content.

### 25.2 Social Profiles and Structured Data

LinkedIn and Instagram currently point to Alexander Minkin's profiles.

Do not automatically represent personal social profiles as official corporate profiles in `Organization.sameAs` unless this is intentionally approved later.

They may be associated with the founder through `Person` structured data.

---

## 26. GEO / AI Search Requirements

The site should make the following entities easy to identify:

- MinkinSpace Consulting;
- company services;
- company expertise;
- founder and team information when approved for the current version;
- problems solved by each service;
- relevant experience;
- contact information.

Requirements:

- factual and explicit service descriptions;
- consistent naming;
- semantic headings;
- descriptive internal links;
- structured data where relevant;
- server-rendered business-critical content;
- FAQ and explanatory sections where useful;
- no hidden critical content that only appears after client-side API calls.

---

## 27. Accessibility

Target WCAG 2.2 AA where reasonably achievable.

Required:

- semantic HTML;
- keyboard navigation;
- visible focus states;
- correct labels for form inputs;
- meaningful alt text;
- decorative images ignored by assistive technologies;
- sufficient color contrast;
- no hover-only interaction;
- logical heading structure;
- reduced-motion preferences respected.

MUI defaults may be used as a foundation but do not replace accessibility testing.

---

## 28. Responsive Requirements

The website must support at minimum:

```text
320 px
375 px
768 px
1024 px
1440 px
```

Use MUI breakpoints centrally through the theme.

The layout must remain usable from 320 px viewport width.

---

## 29. Performance Requirements

Objectives:

- strong Core Web Vitals;
- optimized images;
- responsive image sizing;
- lazy loading for below-the-fold media;
- minimal third-party JavaScript;
- no unnecessary global client state;
- no large background videos in MVP;
- avoid layout shifts;
- keep client bundles small.

Preferred Lighthouse targets:

```text
Performance >= 90
Accessibility >= 90
Best Practices >= 90
SEO >= 90
```

These are quality goals, not strict blockers when a justified integration affects scoring.

---

## 30. Security Requirements

### 30.1 General

- HTTPS in production.
- Secrets only in environment variables or deployment secret management.
- No secrets in browser bundles.
- Server-side Zod validation for submitted data.
- Rate limiting or equivalent abuse protection for login and public submission endpoints.
- Safe error responses.
- Dependency review before production release.
- No direct database exposure to the browser.

### 30.2 Admin

- Better Auth session verification server-side.
- No public registration.
- Every mutation route requires authorization.
- Secure session cookies in production.
- Admin pages use `noindex, nofollow`.
- Admin pages excluded from sitemap.
- State-changing operations must not rely on client-side authorization.
- Rich text, if implemented, must be sanitized against stored XSS.
- Media uploads must validate type and size.
- Authentication logs must not contain passwords, session tokens or secrets.

### 30.3 S3 Storage

S3 credentials must be server-only.

Uploads should use either:

- server-mediated upload through API routes; or
- short-lived presigned URLs generated only after admin authorization.

Do not expose permanent privileged S3 credentials in frontend code.

---

## 31. Environment Variables

Create `.env.example` containing names only, never real secrets.

Expected configuration groups:

```text
DATABASE_URL
BETTER_AUTH_SECRET
BETTER_AUTH_URL
S3_ENDPOINT
S3_REGION
S3_BUCKET
S3_ACCESS_KEY_ID
S3_SECRET_ACCESS_KEY
S3_PUBLIC_BASE_URL
NEXT_PUBLIC_SITE_URL
```

Additional variables may be added for analytics or future integrations.

---

## 32. Analytics

The application should be prepared to track:

- page views;
- CTA clicks;
- service page visits;
- contact form starts;
- contact form submissions;
- outbound social/contact clicks.

Analytics provider is not fixed in the current stack and remains a later integration decision.

Do not add an analytics dependency until a provider is selected.

---

## 33. Legal and Privacy

Before production launch, determine requirements based on:

- company jurisdiction;
- hosting/data-storage jurisdiction;
- target visitor jurisdictions;
- contact form processing;
- analytics provider;
- cookies.

Possible required items:

- Privacy Policy;
- Cookie Policy;
- cookie consent;
- personal-data processing consent;
- legal company details.

Do not invent legal requirements in implementation code before they are confirmed.

---

## 34. Testing Requirements

### 34.1 Functional

Test:

- all public routes;
- navigation;
- AI for Business and Marketing navigation items;
- mobile menu;
- CTAs;
- LinkedIn link;
- Instagram link;
- contact form validation;
- contact form success/error;
- 404 page;
- admin login/logout;
- unauthorized redirect;
- page editing;
- service editing;
- settings editing;
- media upload;
- media validation;
- contact submission viewing;
- destructive-action confirmation.

### 34.2 Technical

Required checks:

- `npm install` succeeds;
- lint passes;
- TypeScript check passes;
- production build succeeds;
- Prisma migrations apply successfully;
- Prisma seed works on a clean database;
- no major console errors;
- no broken internal links;
- sitemap excludes admin routes;
- robots rules are correct;
- protected API endpoints reject unauthorized requests;
- admin content changes appear correctly on public pages.

### 34.3 Responsive

Test at:

```text
320
375
768
1024
1440
```

### 34.4 Accessibility

Test:

- keyboard navigation;
- focus states;
- form labels;
- color contrast;
- dialogs and menus;
- basic screen-reader semantics.

---

## 35. Error and Empty States

Required:

- custom 404 page;
- contact form error state;
- admin login error state;
- admin save error state;
- unauthorized state;
- empty service/media/admin lists;
- image upload failure state.

Optional:

- custom 500 page.

---

## 36. Deployment Requirements

The architecture must support deployment of:

```text
Next.js application
PostgreSQL database
S3-compatible Object Storage
```

Specific hosting provider is not yet fixed.

Deployment must provide:

- Node.js-compatible Next.js runtime;
- persistent PostgreSQL;
- network access to S3-compatible storage;
- HTTPS;
- environment-variable/secret management;
- database migration step;
- production build;
- domain configuration;
- backup strategy for PostgreSQL;
- retention/backup strategy for S3 media.

Docker and Nginx are not mandatory project technologies. They may be introduced later only if the selected hosting environment requires them.

---

## 37. Documentation Requirements

Repository must include `README.md` describing:

- project purpose;
- fixed technology stack;
- prerequisites;
- npm installation;
- local development;
- environment variables;
- PostgreSQL setup;
- Prisma migrations;
- Prisma seed;
- Better Auth admin setup;
- S3 configuration;
- development command;
- production build command;
- deployment process;
- content management process;
- backup/restore process.

Recommended docs:

```text
docs/architecture.md
docs/database.md
docs/admin.md
docs/deployment.md
docs/seo.md
docs/open-questions.md
```

---

## 38. Codex / AI Agent Rules

### 38.1 Mandatory Stack Constraint

Codex must not replace or migrate away from:

```text
Next.js Pages Router
TypeScript
Material UI
React Hook Form
Zod
Next.js API Routes
Better Auth
Prisma ORM
PostgreSQL
S3-compatible Object Storage
npm
```

without an explicit new instruction from the project owner.

### 38.2 Before Coding

Codex must:

1. Read this specification completely.
2. Inspect the current repository.
3. Read `package.json` and existing project conventions.
4. Reuse existing components before adding duplicates.
5. Inspect Prisma schema before modifying data access.
6. Inspect existing Zod schemas before adding validation.
7. Record non-blocking unknowns in `docs/open-questions.md`.

### 38.3 During Implementation

Codex must:

- use TypeScript;
- keep public and admin code clearly separated;
- keep business content in PostgreSQL where it is intended to be editable;
- use Prisma for database access;
- use Better Auth for authentication;
- use React Hook Form + Zod for forms;
- use Material UI as the primary UI system;
- store media in S3-compatible storage, not PostgreSQL;
- keep secrets server-only;
- validate every mutation server-side;
- avoid introducing unnecessary dependencies;
- preserve accessibility;
- preserve responsive behavior;
- keep service pages data-driven;
- never invent company statistics, testimonials, clients or results;
- mark missing approved content as `TODO_CONTENT`;
- not silently change architectural decisions.

### 38.4 After Each Feature

Codex must:

1. run lint/type/build checks relevant to the change;
2. fix introduced errors;
3. test the changed route;
4. verify authorization for protected features;
5. verify responsive behavior;
6. summarize changed files;
7. record unresolved issues.

---

## 39. MVP Acceptance Criteria

### 39.1 Public Pages

- [ ] Main Page
- [ ] About Us
- [ ] Services overview
- [ ] Business Process Automation
- [ ] AI Pre-Sales
- [ ] IT Infrastructure Audit
- [ ] Marketing AI Analysis
- [ ] AI Search & GEO
- [ ] Social Marketing
- [ ] AI for Business
- [ ] Marketing
- [ ] Contact
- [ ] 404

### 39.2 Public UI

- [ ] Header
- [ ] Footer
- [ ] AI for Business navigation
- [ ] Marketing navigation
- [ ] Mobile navigation
- [ ] Global CTA
- [ ] LinkedIn link
- [ ] Instagram link
- [ ] Responsive layouts

### 39.3 Admin

- [ ] `/admin/login`
- [ ] Protected `/admin`
- [ ] Page management
- [ ] Service management
- [ ] Media management
- [ ] SEO management
- [ ] Site settings
- [ ] Social-link management
- [ ] Contact-submission viewing
- [ ] Logout

### 39.4 Data and Storage

- [ ] PostgreSQL configured
- [ ] Prisma schema created
- [ ] Prisma migrations created
- [ ] Seed data includes six services
- [ ] Initial site settings include LinkedIn and Instagram URLs
- [ ] S3-compatible storage configured
- [ ] Media metadata stored in PostgreSQL
- [ ] Media binary files stored outside PostgreSQL

### 39.5 Authentication and Security

- [ ] Better Auth configured
- [ ] No public admin registration
- [ ] Admin route protection server-side
- [ ] Protected mutations verify authorization
- [ ] Secure session handling
- [ ] Login abuse protection
- [ ] Zod validation on mutation endpoints
- [ ] S3 credentials server-only
- [ ] Admin excluded from sitemap
- [ ] Admin uses `noindex, nofollow`

### 39.6 Contact Form

- [ ] React Hook Form implemented
- [ ] Zod validation client-side
- [ ] Zod validation server-side
- [ ] Submission saved through Prisma
- [ ] Success state
- [ ] Error state

### 39.7 SEO / GEO

- [ ] Unique titles
- [ ] Unique descriptions
- [ ] H1 structure
- [ ] Canonical URLs
- [ ] Open Graph metadata
- [ ] XML sitemap
- [ ] robots.txt
- [ ] structured data where relevant
- [ ] core business content server-rendered

### 39.8 Quality

- [ ] `npm` is the package manager
- [ ] TypeScript has no blocking errors
- [ ] Production build succeeds
- [ ] No major console errors
- [ ] No broken internal links
- [ ] 320 px layout works
- [ ] Keyboard navigation works
- [ ] Images optimized
- [ ] README complete
- [ ] No secrets committed

---

## 40. Open Decisions

The technology stack is no longer an open decision.

Remaining product/design/infrastructure decisions:

### Product

- [ ] Final primary CTA wording
- [ ] Final service copy
- [ ] Pricing visibility
- [ ] Cases in MVP or later
- [ ] Single-language or multilingual launch

### Branding

- [ ] Approve/refine Forward Orbit logo
- [ ] Create SVG logo assets
- [ ] Final color palette
- [ ] Typography
- [ ] Illustration/icon style
- [ ] Photography approach

### Infrastructure

- [ ] Hosting provider
- [ ] PostgreSQL provider / deployment method
- [ ] S3-compatible storage provider
- [ ] Production domain
- [ ] Backup policy
- [ ] Error monitoring provider
- [ ] Analytics provider

### Contact Integrations

- [ ] Whether database-only submission handling is sufficient for launch
- [ ] Email notifications
- [ ] CRM integration
- [ ] Telegram/webhook integration

### Legal

- [ ] Company legal details
- [ ] Privacy Policy
- [ ] Cookie Policy
- [ ] Consent requirements
- [ ] Data-storage jurisdiction requirements

---

## 41. Implementation Phases

### Phase 1 — Foundation

- initialize Next.js Pages Router project;
- configure TypeScript;
- configure npm scripts;
- configure Material UI theme;
- configure PostgreSQL;
- configure Prisma;
- create initial migration;
- create seed data;
- configure Better Auth;
- configure S3 storage client;
- create base layout and routing.

### Phase 2 — Public Website

- Header;
- Footer;
- Main Page;
- About Us;
- Services overview;
- reusable service page;
- six service records/pages;
- AI for Business navigation page or section;
- Marketing navigation page or section;
- Contact;
- LinkedIn / Instagram integration.

### Phase 3 — Admin

- login;
- route protection;
- dashboard;
- page editor;
- service editor;
- site settings;
- SEO editor;
- contact submissions.

### Phase 4 — Media

- S3 upload integration;
- media library;
- image selection;
- alt text;
- deletion protection;
- logo management.

### Phase 5 — SEO / GEO / Quality

- metadata;
- structured data;
- sitemap;
- robots.txt;
- accessibility review;
- responsive review;
- performance review;
- production build validation.

### Phase 6 — Deployment

- provision PostgreSQL;
- provision S3-compatible storage;
- configure secrets;
- run migrations;
- seed initial content if required;
- create administrator securely;
- deploy Next.js application;
- configure domain and HTTPS;
- verify backups;
- complete production acceptance checklist.

---

## 42. Definition of Done

The MVP is done when:

1. All required public routes work.
2. All six service pages are database-driven.
3. Public content is rendered server-side.
4. The administrator can log in securely.
5. Routine website content can be edited from `/admin`.
6. Media can be uploaded to S3-compatible storage.
7. LinkedIn and Instagram URLs are editable in settings and rendered publicly.
8. Contact submissions are validated and stored in PostgreSQL.
9. Prisma migrations and seed work from a clean database.
10. SEO, sitemap and robots configuration are implemented.
11. Admin routes are protected and excluded from indexing.
12. The project builds successfully with npm.
13. README documents local setup and deployment.
14. No architectural technology outside the fixed stack has been introduced without approval.
