# Project Subagents

This folder contains project-specific runtime subagent definitions for the MinkinSpace Consulting website.

These files are not installed Codex skills and are not MCP definitions. They describe how the main agent should delegate work when runtime subagent tooling is available.

## Decision

Use a limited subagent model for this project.

For the current landing MVP, the active technical specification is `docs/tech_spec/landing_technical_specifications.md`. The full corporate website specification is future scope only.

Useful bounded workstreams:

- Figma landing design and visual approval;
- public landing frontend implementation;
- contact API and validation;
- SEO / GEO;
- QA and deployment readiness.

The main agent remains coordinator and final integrator.

## Available Project Subagents

- `design-figma.md` - landing Figma layout, visual structure, brand consistency, responsive design, and approval readiness.
- `frontend.md` - public landing Pages Router UI, Material UI components, responsive layout, navigation, forms, and rendering.
- `backend-admin.md` - landing contact API and future-only admin/database notes.
- `seo-geo.md` - SEO metadata, canonical URL, sitemap, robots, structured data, semantic headings, and GEO review.
- `qa-deployment.md` - verification, accessibility, responsive QA, contact API checks, and launch readiness.

## Delegation Rules

- Spawn subagents only for concrete, bounded tasks that can run in parallel.
- Do not delegate the immediate blocking task if the main agent needs the result before moving forward.
- Assign disjoint file or module ownership during implementation.
- Tell subagents that other agents or the user may be editing the repo and they must not revert unrelated changes.
- Do not duplicate the same task across multiple subagents.
- Close runtime subagents when their result has been integrated or is no longer needed.

## Project Phases

Before Figma approval:

- use only Design / Figma and SEO / GEO review subagents when useful;
- do not use implementation subagents for app code.

After Figma approval:

- use Frontend and Contact API workstreams for landing implementation;
- use SEO / GEO and QA / Deployment subagents for independent review.

Before production launch:

- use QA / Deployment, SEO / GEO, and contact API/security review;
- production-changing actions still require explicit owner approval.

## Forbidden

- Do not create a top-level `skills/` directory for project files, rules, or notes.
- Do not create project files under `.agents/skills/`; that path is reserved for complete installed Agent Skill directories managed by the skills CLI.
- Do not create a top-level `mcp/` directory unless it contains real MCP artifacts.
- Do not create fake credentials, fake MCP connection metadata, fake plugins, or fake installed skills.
- Do not add architecture outside the active landing stack.
