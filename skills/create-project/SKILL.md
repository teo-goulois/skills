---
name: create-project
description: Designs and scaffolds a new software project from a product brief. Use when the product shape should determine the stack, structure, and initial AI context instead of cloning a fixed starter.
---

# Create Project

Turn a product idea into the smallest suitable project and leave it understandable
to the next AI agent.

## Load only what applies

The detailed preferences are authored in the public code handbook. This skill
ships generated snapshots under `references/`, so always read the local files
and remain usable without network access. The linked handbook pages are the
canonical upstream sources; update snapshots through `pnpm knowledge:build`,
never by editing generated references.

- TypeScript application: read
  [references/stack-policy.md](references/stack-policy.md) and
  [references/typescript.md](references/typescript.md). Canonical sources:
  [TypeScript stack](https://teogoulois.com/code/stacks/typescript.md) and
  [TypeScript](https://teogoulois.com/code/web/typescript.md).
- TypeScript web surface: also read
  [references/typescript-web.md](references/typescript-web.md). Canonical source:
  [Web conventions](https://teogoulois.com/code/web/conventions.md).
- Web surface with forms: also read
  [references/forms.md](references/forms.md). Canonical source:
  [Forms](https://teogoulois.com/code/web/ui/forms.md).
- Free human support email on a Cloudflare-managed domain: read
  [references/support-email.md](references/support-email.md). Canonical source:
  [Support email](https://teogoulois.com/code/web/support-email.md).
- Before publishing a public landing page: read
  [references/check.md](references/check.md). Canonical source:
  [Launch checklist](https://teogoulois.com/code/web/launch-checklist.md).
- When a public site or product needs analytics: read
  [references/analytics.md](references/analytics.md). Canonical source:
  [Analytics](https://teogoulois.com/code/web/analytics.md).
- After scaffolding: read
  [references/project-foundation.md](references/project-foundation.md).
  Canonical source:
  [Project context for agents](https://teogoulois.com/code/agents/project-context.md).

For another ecosystem, keep this workflow but use its native tools and
conventions. Do not force Better-T-Stack or TypeScript onto it.

## Rules

- Product constraints and explicit user choices override preferences.
- Prefer the documented defaults when two choices fit equally well.
- Keep the architecture as small as the product allows.
- Do not ask the user to choose technologies they do not understand.
- Match vocabulary, detail, and questions to the user's declared technical
  level.
- Treat the confirmed brief and durable decisions as project state, not chat
  history.
- Validate before writing and never overwrite a non-empty target without
  approval.
- Do not create remote infrastructure, accounts, secrets, or deployments unless
  requested.

## Workflow

1. **Calibrate** — first check durable user memory, then
   `~/.config/create-project/preferences.json`, for `technicalLevel` and
   `language`. If a valid level exists, use it silently. Otherwise the first
   reply must ask only whether the user is technical or non-technical, then
   persist the answer and current language. Never copy personal preferences into
   the project.
   - Technical: use precise terminology, expose meaningful tradeoffs, and accept
     technology preferences.
   - Non-technical: speak in product language, never ask the user to select a
     framework, database, hosting provider, or architecture, and make those
     choices autonomously.
2. **Onboard** — in the next reply, ask one short message for the pitch, project
   name if one exists, target user, initial surfaces, and known product
   constraints. Adapt examples and wording to the selected level. If there is no
   name, understand the pitch first, then propose three relevant names. Ask
   follow-ups only when an answer can materially change the product or
   architecture.
3. **Confirm** — summarize the product, first-release scope, assumptions, and
   chosen name. For a customer-facing product, also resolve the intended support
   channel and owner without forcing infrastructure choices on a non-technical
   user. Get the user's confirmation.
4. **Decide** — give one recommended stack, its main compromise, and at most one
   credible alternative. For a non-technical user, explain outcomes and risks in
   plain language rather than listing implementation details. State which
   preferences were overridden.
5. **Plan** — map the decision to an explicit generator configuration. Include
   `none`, empty arrays, booleans, package manager, and deployment fields rather
   than relying on generator defaults.
6. **Validate and scaffold** — for a compatible TypeScript application, prefer
   the official Better-T-Stack MCP schema and planning tools. Otherwise run the
   current CLI schema and a dry run before creation:

   ```bash
   npx create-better-t-stack@latest schema --name createInput
   npx create-better-t-stack@latest create-json --input '<full-json>' --dry-run
   ```

   After validation, scaffold without an agent-driven interactive prompt.

7. **Establish** — install dependencies, inspect generated commands, keep this
   skill available project-locally, and add only the necessary project context.
   For a web surface, install the project-local interface skills required by the
   web conventions and use the matching skill for interface work. Then run
   format checking, lint, type checks, and the smallest relevant build or test.
8. **Report** — state the resulting stack, intentional deviations, validation
   performed, and commands to continue.
