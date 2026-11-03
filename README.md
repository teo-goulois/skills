# Téo Goulois — Agent Skills

The skills that work with [my code handbook](https://teogoulois.com/code/),
the way Graphical's skills work with `GUI.md`. A project carries its own copy
of the handbook, `HANDBOOK.md` and `handbook/`, installed from the
teogoulois.com registry; the skills read that copy, so they bundle none.

## Skills

- `handbook-build` starts a project from a product brief, and builds new apps,
  packages, and features with the handbook's defaults.
- `handbook-convert` brings existing code in line with the handbook, within an
  agreed scope.
- `handbook-audit` reports, read-only, where a project drifts from the
  handbook and its own decisions.

## Install

Install the skills once, for every project:

```bash
npx skills add teo-goulois/skills --skill handbook-build handbook-convert handbook-audit --global
```

Use `--agent codex`, `--agent claude-code`, or `--agent cursor` to select an
agent explicitly.

Then install the handbook in a project, from its root, with one more item per
platform it has (`handbook-web`, `handbook-mobile`, or `handbook-desktop`):

```bash
npx shadcn@latest add https://teogoulois.com/r/handbook.json https://teogoulois.com/r/handbook-web.json
```

## Sources

The skills are written in the teogoulois repository (`skills/`) and copied
here. The handbook itself is published at https://teogoulois.com/code.
