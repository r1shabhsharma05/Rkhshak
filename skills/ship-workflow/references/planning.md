# Planning — break work into ordered, verifiable tasks

Distilled from the planning-and-task-breakdown skill (MIT, including the merged writing-plans rules). Method in our own words; the full templates live in that source. Use when a spec or clear requirements exist and need breaking into implementable tasks, or when a task feels too large to start.

## The planning process
1. **Enter plan mode.** No code is written while planning. Read the spec, the relevant code, and the constraints first.
2. **Identify the dependency graph.** What depends on what? Name the dependencies explicitly — a task with a hidden dependency is a task that blocks mid-way.
3. **Slice vertically.** Each slice is a thin, end-to-end piece of value (not a layer: not "all the database, then all the UI"). A slice that cannot be demonstrated is not a slice.
4. **Write tasks.** Each task has: a short descriptive title, the files it touches, the steps in order, the verification for each step (test command, expected output), and the done condition. A task without a verification step is a wish.
5. **Order and checkpoint.** Order by dependency, then by risk (riskiest first). Place checkpoints after each phase: the work stops, the state is verified, and only then does the next phase start.

## Task sizing
A task is one focused piece of work: small enough to finish in one session, big enough to be worth verifying on its own. If a task has more than a handful of steps, split it. If two tasks always move together, merge them.

## Output files
- **Task list target:** the plan document lives in a file (implementation plan), not in chat. It names the feature, the architecture decisions, the task list by phase with checkpoints, the risks and mitigations, the open questions, and the parallelization opportunities.
- **Writing plans for an unseen implementer:** the plan must stand alone. Scope check (what is in, what is out), file structure (where things go), step granularity (each step is one action with its verification), a self-review pass (read the plan as the implementer: is any step ambiguous?), and an execution handoff (who runs it, in what order, with what approvals).

## Common rationalizations — do not accept these
- "Planning wastes time" — the plan is what makes the build fast; unplanned work is rework.
- "I will figure out the order as I go" — that is the dependency graph, undiscovered, blocking you later.
- "The tasks are obvious" — write them down anyway; obvious to you is ambiguous to the implementer.

## Red flags
- A plan with no checkpoints.
- A task list that is really a layer list (database, then API, then UI).
- A plan whose first task depends on a decision that is still open.
