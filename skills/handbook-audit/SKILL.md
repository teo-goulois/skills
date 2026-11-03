---
name: handbook-audit
description: Audits an existing project against Téo's handbook and its own decisions, read-only, and reports drift with evidence and the smallest fix. Use to check a project, an area, or a change, to find what an older scaffold misses, or to see what a newer handbook revision would change. Applying the fixes is handbook-convert.
---

# Handbook audit

Find where a project departs from the handbook, tell drift from deliberate
decisions, and plan the smallest fixes. Change nothing: no edits, installs,
migrations, or external state.

## Sources

Use them in this order:

1. what the user asks now;
2. the nearest `AGENTS.md` and the repository's documentation;
3. the decisions in `docs/decisions/`;
4. the established code and test conventions;
5. the handbook: `HANDBOOK.md` and the pages under `handbook/`.

A recorded decision wins over a page: report it as an intentional exception,
not as drift. A project without `HANDBOOK.md` is audited against the site
(https://teogoulois.com/code), and the first finding is the missing install
(see `handbook-build`).

## Workflow

1. **Scope.** Settle the root, the area, and the outcome wanted. Keep a
   focused request focused.
2. **Discover.** Read the instructions, manifests, workspace configuration,
   decisions, commands, and the relevant source. Check the Git status.
3. **Revision.** Compare the installed revision, in `HANDBOOK.md`, with the
   latest one:
   `curl -fsS https://teogoulois.com/r/handbook.json | jq -r .meta.revision`.
   When they differ, read what the latest pages change for the project.
4. **Baseline.** State the product, the stack, the package boundaries, the
   data flow, and the pages that apply. Keep facts, recorded decisions,
   inferred intent, and preferences apart.
5. **Trace** representative runtime paths rather than judging names: route to
   component, component to data client, transport to procedure, procedure to
   storage or external service.
6. **Compare** each applicable area with its page:
   - component placement and shared boundaries; components taken from the
     teogoulois registry before shadcn; icons behind the shared wrapper;
   - routes, forms, server state, API transport, and cache ownership; every
     user action as one procedure, with its MCP tool;
   - auth, validation, authorization, errors, jobs, and integrations;
   - tooling, commands, tests, environment and secrets, local URLs, and
     deployment;
   - analytics coverage: daily use, every feature, accuracy;
   - changelog: user-visible `feat:` or `fix:` commits since the last release
     without a note in `changes/`;
   - project context, launch readiness, and support, when in scope.
7. **Check.** Run the repository's non-mutating format, lint, type, test, and
   build commands, in proportion to the scope. Keep failures that predate the
   area apart from findings.
8. **Report.**

## Report

1. The baseline, the revision (installed and latest), and the checks run.
2. Findings by impact (blocking, important, optional), each with file
   evidence, its page, the smallest fix, and how to verify it.
3. Intentional exceptions, with their decision, and unknowns.
4. An ordered plan for `handbook-convert`.

**Done when** every applicable page is either matched, reported as drift with
evidence, or covered by a recorded decision.
