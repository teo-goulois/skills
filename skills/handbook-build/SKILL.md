---
name: handbook-build
description: Starts a project from a product brief, or adds an app, a package, or a feature to a project, with Téo's handbook defaults. Use for a new project, and for new work in a project that has HANDBOOK.md, even when the request does not mention the handbook. Aligning existing code is handbook-convert; finding drift is handbook-audit.
---

# Handbook build

Build new things the way the handbook says, so the project stays consistent
with itself and with Téo's other projects.

## The handbook

A project carries its own copy: `HANDBOOK.md` at the root, and the pages it
lists under `handbook/`. Read `HANDBOOK.md` first; it says which source wins,
where exceptions live, and how `GUI.md` shares the work. Then read only the
pages that apply to the work.

A project without `HANDBOOK.md` installs it before building:

```sh
npx shadcn@latest add https://teogoulois.com/r/handbook.json
```

Add one platform item per surface the project has:
`https://teogoulois.com/r/handbook-web.json`, `handbook-mobile.json`, or
`handbook-desktop.json`. Then add the pointer `HANDBOOK.md` gives to
`AGENTS.md`. Never edit the installed copy: a project's exception is a
decision in `docs/decisions/`.

## New project

Follow [references/new-project.md](references/new-project.md): it calibrates
on the user, confirms the brief, picks the stack, scaffolds, and installs the
handbook in the new project.

## New work in a project

1. **Read** `HANDBOOK.md`, the pages that apply, the project's `AGENTS.md`, and
   the decisions in `docs/decisions/` that touch the area.
2. **Reuse** what the project already has: its shared packages, UI components,
   API procedures, and patterns. Extend one before writing a parallel one.
3. **Build** with the handbook's defaults where the project has no convention
   of its own. When a better option exists, propose it with its trade-off
   before using it.
4. **Record** a durable departure from a page as a decision in
   `docs/decisions/`, with the page and the reason.
5. **Verify** with the project's own format, lint, type, test, and build
   commands, in proportion to the change.

**Done when** the work follows every page that applies or records why not,
and the project's checks pass.
