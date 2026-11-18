---
name: spec-kit
description: "Build software spec-first: a written specification drives the plan, the tasks, and the code — never the other way round. Constitution → specify → clarify → plan → tasks → analyze → implement → converge, with bug and idea-assessment extensions."
---

# Spec Kit — specification-driven development

## Purpose
Code is the expression of a specification, not the source of truth. A feature starts as a vague idea, becomes a written spec (WHAT + WHY, never HOW), then a plan, then a dependency-ordered task list, then code — each step reviewed before the next begins. When requirements change, the spec changes first and the code follows. That is the whole method: specifications drive code, and code serves specifications.

Use it for a new feature, a new project, or a significant change — anything where getting the intent wrong costs more than writing it down first. Do not force it onto a one-line fix, a copy-paste port, or an explicit "just do it" order; a direct minimal fix is faster there.

## How it works (any user, any project, any stack)
No setup beyond scaffolding (see `references/scaffolding.md`). The agent reads this skill and the references, then runs the steps below one at a time, in order, in the user's conversation — never in the terminal, never several steps at once. Each step's output is reviewed before the next step starts.

## Multi-agent
Works with any agent that reads SKILL.md. The rules are written as plain checks, not model-specific tricks. Where a step names a human review, the human reviews; the agent never approves its own spec, plan, or tasks.

## Workflow
1. **Constitution (once per project).** Write the project's non-negotiable principles first — see `references/constitution.md`. Every later step is checked against it. Standing rules outrank template defaults; record any exception in the constitution itself.
2. **Scope check (only when one request bundles several independently testable capabilities).** If it does, draw a capability map first — see `references/capability-map.md`. Single-capability requests skip this step.
3. **Specify.** Turn the natural-language request into `specs/NNN-name/spec.md` — WHAT users need + WHY, never HOW. Mark every real ambiguity `[NEEDS CLARIFICATION: ...]`, never guess. See `references/specify.md`.
4. **Clarify (optional, before planning).** Ask at most 5 targeted questions, one at a time, and encode each answer back into the spec. See `references/clarify.md`.
5. **Plan.** Spec → `plan.md` + `research.md`, `data-model.md`, `contracts/`, `quickstart.md`. Tech choices carry rationale; constitution gates must pass or be justified in writing. See `references/plan.md`.
6. **Tasks.** Plan → `tasks.md`: dependency-ordered, grouped by user story, `[P]` marks parallel-safe tasks. See `references/tasks.md`.
7. **Analyze (optional, before implementing).** Non-destructive cross-artifact consistency check across spec, plan, and tasks. Read-only — it changes nothing. See `references/analyze.md`.
8. **Checklist (optional).** Quality checklists for the feature's requirements — "unit tests for English". See `references/checklist.md`.
9. **Implement.** Execute `tasks.md` phase by phase, marking each completed task `[X]`. See `references/implement.md`.
10. **Converge.** Assess the codebase against spec/plan/tasks; append any remaining work as new tasks, then repeat implement + converge until the report says `Converged`. See `references/converge.md`.
11. **Extensions (only when needed).** A bug with unclear cause: `references/bug-extension.md` (assess → fix → verify). An idea you are unsure about: `references/assess-extension.md` (intake → research → define → shape → decide).

## The flow, at a glance
```
constitution → specify → clarify → plan → tasks → analyze → implement → converge
     │                                                        ▲              │
     └──────── standing rules outrank template defaults ────┴── repeat until Converged
```

## References
| File | What it covers |
|---|---|
| `references/constitution.md` | The 9 articles, versioning, amendment, standing-rules-outrank-template |
| `references/capability-map.md` | Phase 0 — one request, several independently testable capabilities: module table + build order |
| `references/specify.md` | Writing the spec — WHAT + WHY, NEEDS CLARIFICATION, spec template, quality checklist |
| `references/clarify.md` | Up to 5 questions, one at a time, answers encoded back into the spec |
| `references/plan.md` | Research, data model, contracts, quickstart, constitution gates |
| `references/tasks.md` | Checklist task format, [P] markers, phases by user story |
| `references/analyze.md` | Read-only cross-artifact consistency check, severity, report format |
| `references/checklist.md` | Checklists as unit tests for requirements writing |
| `references/implement.md` | Phase-by-phase execution, checklist gate, marking tasks done |
| `references/converge.md` | Append-only gap closure, converged report, the repeat loop |
| `references/bug-extension.md` | Bug workflow — assess → fix → verify, verdict verified / partial / failed |
| `references/assess-extension.md` | Idea assessment — intake → research → define → shape → decide (go / needs-clarification / kill) |
| `references/scaffolding.md` | New project vs existing project setup, the specify CLI |

## Rules (strict — follow every one)
- **Spec = WHAT + WHY, never HOW.** No tech stack, APIs, or code structure in the spec. A spec that names the implementation is not a spec.
- **[NEEDS CLARIFICATION: ...] — mark every ambiguity, never guess.** A spec with unresolved markers is not ready for plan. At most 3 markers in a spec; at most 5 questions in clarify.
- **One step at a time, reviewed before the next.** Stop after writing the spec. Planning starts only after the spec is approved, in a later turn. Never write the spec and start the plan or code in the same turn.
- **Test-first.** Contracts first, then tests in order contract → integration → e2e → unit, then source to make them pass. Tests are written before the code they test, and confirmed to fail first.
- **No speculative features.** Every feature traces to a user story + acceptance criteria. "Might need it later" is not a reason.
- **Success criteria are measurable and technology-agnostic.** "Users complete checkout in under 3 minutes", not "API responds in under 200ms".
- **The constitution is non-negotiable.** A conflict is fixed by changing the spec, plan, or tasks — never by diluting the principle. Changing a principle needs a separate, explicit constitution update.
- **Standing rules outrank template defaults.** Where the project's own standing rules disagree with a template default, the standing rules win — and the exception is recorded in the constitution.
- **Analyze is read-only. Converge is append-only.** Analyze changes no file. Converge only appends a new Convergence phase to `tasks.md`; it never rewrites, renumbers, or deletes an existing task, and never touches `spec.md` or `plan.md`.
- **Only `verified` counts.** A bug fix is done only when the original symptom no longer reproduces and all critical checks pass. `partial` and `failed` are not done.
- **Killing an idea is a success.** The assess extension exists to stop weak ideas early, with a documented reason — not to push every idea through.

## Provenance
Summarized in our own words from GitHub Spec Kit (github/spec-kit, MIT) and its `spec-driven.md` methodology — constitution → specify → clarify → plan → tasks → analyze/checklist → implement → converge, plus the bug and assess extensions. The capability-map step and the gated human-review-per-phase rule come from the spec-driven-development method, merged here because they are the same spec-first workflow. The full method, templates, and CLI live in the Spec Kit repo.
