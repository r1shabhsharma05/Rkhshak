# Tasks

Plan → executable task list at `tasks.md`, ready for an agent to execute without context beyond the feature's design documents.

## Inputs

- **Required:** `plan.md` (tech stack, libraries, structure), `spec.md` (user stories with priorities P1, P2, P3…).
- **Optional:** `data-model.md`, `contracts/`, `research.md`, `quickstart.md`. Generate from whatever exists.
- **If present:** the constitution.

## Checklist format (required)

Every task follows this exact format:

```text
- [ ] [TaskID] [P?] [Story?] Description with file path
```

- **Checkbox:** always `- [ ]`.
- **Task ID:** sequential in execution order: T001, T002, T003…
- **[P] marker:** only if the task is parallel-safe — different files, no dependencies on incomplete tasks.
- **[Story] label:** required for user-story phase tasks only (`[US1]`, `[US2]`…). Setup, Foundational, and Polish phases carry no story label.
- **Description:** a clear action with the exact file path.

Examples — correct:

```text
- [ ] T001 Create project structure per implementation plan
- [ ] T005 [P] Implement authentication middleware in src/middleware/auth.py
- [ ] T012 [P] [US1] Create User model in src/models/user.py
- [ ] T014 [US1] Implement UserService in src/services/user_service.py
```

Wrong: missing ID, missing story label in a story phase, missing checkbox, missing file path.

## Organization

Tasks are organized **by user story** — this is what makes stories independently implementable and testable.

- **Phase 1 — Setup:** project initialization, shared infrastructure.
- **Phase 2 — Foundational:** blocking prerequisites for all user stories; must complete before any story phase.
- **Phase 3+ — one phase per user story**, in priority order. Within each story: tests (if requested) → models → services → endpoints → integration. Each phase is a complete, independently testable increment.
- **Final phase — Polish & cross-cutting concerns.**

Mapping rules:

- **From user stories:** each story gets its models, services, interfaces/UI, and (if requested) its tests. Mark story dependencies; most stories should be independent.
- **From contracts:** each interface contract maps to the user story it serves. If tests are requested, each contract gets a contract-test task `[P]` before its implementation task in that story's phase.
- **From the data model:** each entity maps to the story (or stories) that need it; an entity serving several stories goes in the earliest story or Setup. The data model is the canonical source for field constraints (max/min length, nullable/required, enum values, validation rules, including constraints encoded in field types). Cite each constrained field explicitly using `data-model.md` and its exact `Entity.field` in the implementing task — cite, do not duplicate the constraint prose. A task-specific constraint must not contradict the canonical definition. Every constrained field must have an explicit resolving citation in at least one implementing task.
- **From research:** decisions become setup tasks.

## Tests are optional here

Generate test tasks only if the spec explicitly requests them or the user asks for a test-driven approach. When tests are requested, they follow the test-first order: contracts first, then contract → integration → e2e → unit.

## Completion report

Path to `tasks.md` plus: total task count, count per user story, parallel opportunities identified, independent test criteria per story, suggested MVP scope (typically just User Story 1), and format validation confirming every task follows the checklist format.
