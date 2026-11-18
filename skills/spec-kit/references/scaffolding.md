# Scaffolding

Set up Spec Kit in a project with the `specify` CLI (from the Spec Kit project — clone the repo and install the CLI per its own README; the CLI is the supported install path, not a hand-copied template).

## New project

```bash
specify init my-project --ignore-agent-tools --non-interactive
```

Creates the project with `.specify/` scaffolding (templates, scripts, workflows, memory). The `--ignore-agent-tools` flag skips agent-specific files for agents that read command files directly instead of using native integration.

## Existing project

From the project root:

```bash
specify init . --ignore-agent-tools --non-interactive
```

Same scaffolding, added to the existing tree. Verify the scaffold landed (`.specify/` present with templates, scripts, workflows, memory) before running the first specify step.

## What the scaffold contains

- `.specify/` — templates, scripts, workflows, memory (including `.specify/memory/constitution.md` once created).
- `specs/` — one directory per feature (`specs/NNN-name/`), holding `spec.md`, `plan.md`, `research.md`, `data-model.md`, `contracts/`, `quickstart.md`, `tasks.md`, and `checklists/`.
- `.specify/assessments/` — one directory per assessed idea (`<slug>/intake.md`, `research.md`, `problem.md`, `decision.md`).

## Extensions

Install from the project directory only when needed:

- `specify extension add bug` — bug workflow (assess → fix → verify). See `references/bug-extension.md`.
- `specify extension add assess` — idea assessment (intake → research → define → shape → decide). See `references/assess-extension.md`.

## First run

1. Create or update the constitution (once per project).
2. Run specify for the first feature; review the spec before planning.
3. Run the steps one at a time, in order, reviewing each result before continuing.
