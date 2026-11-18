# Constitution

The constitution is the project's architectural DNA: a short set of non-negotiable principles, written once per project, that every spec, plan, and task is checked against. It lives at `.specify/memory/constitution.md`.

## The 9 articles

| Article | Principle |
|---|---|
| I — Library-first | Every feature begins as a standalone library with clear boundaries, not inline application code. |
| II — CLI interface | Every library exposes its functionality through a command-line interface: text in, text out, JSON for structured data. |
| III — Test-first | No implementation code before tests exist, are approved, and are confirmed to fail. Non-negotiable. |
| IV–VI — Project-defined | Defined by each project, not prescribed. Typical concerns: integration testing, observability, versioning, breaking changes, security boundaries. Fill these slots with the project's own standards. |
| VII — Simplicity | Minimal structure: at most 3 projects for initial implementation; more needs documented justification. No future-proofing. |
| VIII — Anti-abstraction | Use framework features directly rather than wrapping them. One model representation, no speculative layers. |
| IX — Integration-first | Prefer real databases over mocks, real service instances over stubs. Contract tests are mandatory before implementation. |

Articles IV–VI are placeholders by design: the nine-article shape stays stable while each project encodes its own standards in them.

## Writing / amending it

- Create it from the user's stated principles plus what can be inferred from the project (README, docs, prior versions). Every principle gets a succinct name, a paragraph of non-negotiable rules, and a rationale where it is not obvious.
- **Scope guard:** this step updates the constitution only. Feature work, code, refactoring, or deployment requests in the same input are deferred intents — list them as next actions with the follow-up step, do not execute them here.
- **Versioning (semantic):** MAJOR for backward-incompatible removals or redefinitions, MINOR for a new or materially expanded principle, PATCH for clarifications and wording. Record the ratification date (original adoption) and the last-amended date (today when changed).
- **Amendment process:** a change needs a documented rationale, review and approval by the project maintainers, and a backwards-compatibility assessment. After an update, write a short sync-impact report (old → new version, principles changed/added/removed, follow-up TODOs) for human review; it is scratch material, not governance content.
- No bracketed placeholder tokens left unexplained. If a value is genuinely unknown, write `TODO(<FIELD>): explanation` and list it in the sync-impact report.

## Standing rules outrank template defaults

A project's own standing rules (its working agreements, quality bars, verification habits) outrank the template defaults in the constitution template. Where they disagree, the standing rules win — and the exception is recorded in the constitution so the conflict is visible, not silent.

## Enforcement

- The plan step runs constitution gates (simplicity ≤3 projects, no future-proofing, framework used directly, contracts defined) and errors on unjustified violations.
- Analyze treats a constitution conflict as automatically CRITICAL.
- Converge treats code violating a MUST principle as its highest-severity finding.
- A principle itself changes only in a separate, explicit constitution update — never silently inside analyze, plan, or converge.
