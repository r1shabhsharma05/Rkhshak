# Plan

Spec → implementation plan. The command ends after Phase 1 design; it produces `plan.md` plus supporting artifacts, not code.

## Inputs

Read the spec and the constitution. Load the plan template. Fill the Technical Context section, marking unknowns as `NEEDS CLARIFICATION`.

## Constitution gates (Phase -1)

Evaluate before designing; error on unjustified violations:

- **Simplicity gate (Article VII):** using ≤3 projects? No future-proofing?
- **Anti-abstraction gate (Article VIII):** using framework features directly? Single model representation?
- **Integration-first gate (Article IX):** contracts defined? Contract tests written?

A gate failure must be documented with justification in a Complexity Tracking section — or the design changes until the gate passes. Re-evaluate the gates after the design is complete.

## Phase 0 — Research (`research.md`)

For each unknown in Technical Context, each dependency, and each integration: research it and consolidate findings as:

- **Decision:** what was chosen
- **Rationale:** why
- **Alternatives considered:** what else was evaluated

Output: `research.md` with all `NEEDS CLARIFICATION` items resolved.

## Phase 1 — Design & contracts

Prerequisites: `research.md` complete.

1. **Data model (`data-model.md`).** Extract entities from the spec: name, fields, relationships, validation rules from requirements, state transitions where applicable.
2. **Contracts (`contracts/`).** For every interface the project exposes to users or other systems — public APIs for libraries, command schemas for CLIs, endpoints for web services, grammars for parsers, UI contracts for applications. Skip only if the project is purely internal (build scripts, one-off tools). Contracts are the canonical source for field constraints; tasks cite them, they do not duplicate them.
3. **Quickstart (`quickstart.md`).** A runnable validation guide: prerequisites, setup and run commands, expected outcomes, key validation scenarios proving the feature works end to end. Link to contracts and the data model instead of duplicating them. No full implementation code, no model/service/controller bodies, no migrations, no complete test suites — those belong in `tasks.md` and implementation.

## Key rules

- Keep the plan high-level and readable. Code samples, detailed algorithms, and extensive technical specifications go in the appropriate detail file, not the plan.
- Every technology choice has documented rationale and traces back to a specific requirement.
- Use project-relative paths in documentation.
- Error on gate failures or unresolved clarifications — do not paper over them.

## Completion report

Branch, `plan.md` path, and the generated artifacts (`research.md`, `data-model.md`, `contracts/`, `quickstart.md`).
