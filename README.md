# Téo Goulois — Agent Skills

Project-local agent skills generated from [my code handbook](https://teogoulois.com/code/).
Each skill bundles the relevant handbook snapshots so it remains usable without
network access after installation.

## Skills

- `create-project` turns a product brief into the smallest suitable new project.
- `update-project` audits and incrementally realigns an existing codebase.

## Install

Install one skill from the root of the target project:

```bash
npx skills add teo-goulois/skills --skill create-project
```

```bash
npx skills add teo-goulois/skills --skill update-project
```

The installer detects supported agents and installs into the project by default.
Use `--agent codex`, `--agent claude-code`, or `--agent cursor` to select one
explicitly.

## Sources

The public handbook is the canonical source for preferences and conventions.
Files under `references/` are generated offline snapshots and should not be
edited directly.
