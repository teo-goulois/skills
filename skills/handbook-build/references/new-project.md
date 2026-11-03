# New project

Turn a product idea into the smallest suitable project, and leave it
understandable to the next agent.

The stack and structure come from the handbook. Before the project exists,
read the pages on the site: [Stack](https://teogoulois.com/code/stack/index.md),
then the platform pages the surfaces need
([Web](https://teogoulois.com/code/web/index.md),
[Mobile](https://teogoulois.com/code/mobile.md),
[Desktop](https://teogoulois.com/code/desktop.md)). For another ecosystem,
keep this workflow with its native tools: do not force Better-T-Stack or
TypeScript onto it.

## Rules

- Product constraints and explicit user choices override the handbook.
- Keep the architecture as small as the product allows.
- Match vocabulary, detail, and questions to the user's technical level. A
  non-technical user never chooses a framework, a database, a host, or an
  architecture: you choose.
- Treat the confirmed brief and durable decisions as project state, not chat
  history.
- Validate before writing, and never overwrite a non-empty target without
  approval.
- Create remote infrastructure, accounts, secrets, or deployments only when
  asked.

## Workflow

1. **Calibrate.** Look for `technicalLevel` and `language` in durable user
   memory, then in `~/.config/create-project/preferences.json`. If a valid
   level exists, use it silently. Otherwise the first reply only asks whether
   the user is technical or not, then stores the answer and the language there.
   Never copy personal preferences into the project.
2. **Onboard.** In one short message, ask for the pitch, the name if one
   exists, the target user, the first surfaces, and known constraints. With no
   name, understand the pitch first, then propose three. Ask a follow-up only
   when the answer can change the product or the architecture.
3. **Confirm.** Summarize the product, the first-release scope, the
   assumptions, and the name. For a customer-facing product, settle the support
   channel and its owner. Wait for the user's yes.
4. **Decide.** Give one recommended stack, its main trade-off, and at most one
   credible alternative. For a non-technical user, explain outcomes and risks,
   not implementation. Say which handbook defaults you overrode.
5. **Plan.** Map the decision to an explicit generator configuration: include
   `none`, empty arrays, booleans, the package manager, and deployment fields
   rather than relying on generator defaults.
6. **Scaffold.** For a compatible TypeScript application, prefer the
   Better-T-Stack MCP schema and planning tools. Otherwise check the CLI schema
   and run a dry run first:

   ```sh
   npx create-better-t-stack@latest schema --name createInput
   npx create-better-t-stack@latest create-json --input '<full-json>' --dry-run
   ```

   Then scaffold without an interactive prompt.

7. **Establish.** In the new project's root:
   - install the handbook and its platform items (see `SKILL.md`), and add its
     pointer to `AGENTS.md`;
   - write the context that the installed `handbook/agents/project-context.md`
     asks for: `AGENTS.md`, `docs/product-vision.md`, and
     `docs/decisions/001-stack.md`;
   - for a project with a UI, offer a Graphical theme (`GUI.md`) when none is
     chosen yet.

   Skills come from the user's global setup, never from the project.

8. **Verify.** Install dependencies, then run format, lint, type checks, and
   the smallest relevant build or test.
9. **Report** the stack, the deviations and why, what was verified, and the
   commands to continue.

**Done when** the project builds, `HANDBOOK.md` and its pointer are in place,
and the brief and the stack decision are written in `docs/`.
