# Converge

Close the gap between what a feature's specification, plan, and tasks call for and what the codebase currently implements. Runs only after implement has run on the current `tasks.md`, and after tasks generation has produced a complete `tasks.md`.

## Operating constraints

- **Append-only, never rewrite.** The only write is appending a new `## Phase N: Convergence` section to `tasks.md`. It must not: modify `spec.md` or `plan.md` in any way; rewrite, renumber, reorder, or delete any existing task (including tasks from a prior Convergence phase); modify, create, or delete any application code — completing the appended tasks is implement's job.
- **Not a diff tool.** It assesses the present state of the code relative to the feature's artifacts — no branch comparison, no history.
- **Constitution authority is non-negotiable.** Code violating a MUST principle is the highest-severity finding and produces a remediation task. If the constitution is an unfilled template, say so and treat its principles as not yet enforceable.

## Execution

1. Load `spec.md`, `plan.md`, and `tasks.md` as the **sole source of intent** (constitution as governing constraints). Read the current state of the code.
2. Determine which requirements, acceptance criteria, plan decisions, and existing tasks are unmet, incomplete, or only partially satisfied.
3. For each gap, write a new, traceable task: what is missing, which spec requirement / plan decision it traces to, and how to verify it. Append them as a new `## Phase N: Convergence` section at the bottom of `tasks.md`.
4. If the codebase already satisfies everything, leave `tasks.md` **byte-for-byte unchanged** (no empty Convergence header) and report a clean result.

## Outcome and the loop

- **Converged:** report `✅ Converged — the implementation satisfies the spec, plan, and tasks.` Recommend proceeding to review. No further implement pass.
- **Tasks appended:** report the outcome (`tasks_appended`), list the appended tasks with their traces, and run implement again on the new tasks, then converge again.

Repeat implement + converge until `Converged`. Each round appends only what is still missing; nothing already done is re-listed.
