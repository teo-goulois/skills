---
name: handbook-convert
description: Brings an existing project in line with Téo's handbook, within an agreed scope, in coherent batches that preserve behavior. Use when asked to align, migrate, update, or refactor a project toward the handbook, or to apply a newer handbook revision. Read-only checks are handbook-audit; new work is handbook-build.
---

# Handbook convert

Apply the handbook to code that already exists, without breaking what it does
or overriding what the project decided on purpose.

## Before changing anything

1. **Scope.** Honor a scope the user already gave. Otherwise ask the question
   in `HANDBOOK.md` once: the whole project, selected areas, or the reference
   only. Wait for the answer. A request about one area never authorizes the
   whole project.
2. **Audit.** Run `handbook-audit` on that scope. Its findings and its plan
   are what you convert; a difference it did not report is not yours to
   change.
3. **Revision.** To apply a newer handbook, first install it over the copy
   (`npx shadcn@latest add <the project's handbook items> --overwrite`, as
   `HANDBOOK.md` says), and read the diff of `handbook/`.

## Rules

- Never rerun a scaffold generator over an existing repository.
- Preserve the user's changes: check the Git status first.
- Keep one migration per batch, apart from unrelated cleanup or formatting.
- Replace a working dependency or stack only for a concrete benefit, with a
  migration path the user agreed to.
- Prefer an existing shared abstraction over a new parallel one.
- Prove behavior at the boundary that matters: a file existing is not proof
  that its runtime path works.
- Record a durable departure from a page as a decision in `docs/decisions/`.
  Never edit `HANDBOOK.md` or `handbook/`.

## Convert

1. Apply the audit's plan in dependency order, one coherent batch at a time.
2. Move one complete vertical slice at a time, and remove the path it
   replaces in the same batch. For a TypeScript web project: framework server
   functions or actions become one oRPC procedure, with its MCP tool and
   reused `queryOptions` and `mutationOptions`; components come from the
   teogoulois registry; direct icon imports move behind the shared wrapper,
   one surface at a time.
3. After each batch, run the focused checks, then the smallest meaningful
   wider one, and read the diff for unrelated churn.

## Report

Track every finding in scope as **converted**, **already matched**,
**intentional exception** (with its decision), or **blocked** (with the
reason). Then give the files and decisions changed, the checks run with
failures that predate the work, and the next batch.

**Done when** every finding in scope has one of those four states, with
evidence.
