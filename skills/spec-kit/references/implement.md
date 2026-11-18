# Implement

Execute `tasks.md` end to end. Assumes a complete task breakdown exists; if tasks are incomplete or missing, say so and suggest running tasks generation first — do not invent tasks.

## Checklist gate (first)

If `checklists/` exists under the feature directory, treat checklist markers as a **read-only gate**: scan checkbox state, report it, ask before proceeding when needed. **Do not modify checklist files or markers.**

| Checklist | Total | Checked | Unchecked | Status |
|-----------|-------|---------|-----------|--------|
| ux.md | 12 | 12 | 0 | ✓ PASS |
| security.md | 6 | 6 | 0 | ✓ PASS |

- **PASS:** all checklists have 0 unchecked items → proceed.
- **FAIL:** one or more checklists have unchecked items → show the table and **stop** and ask: "Some checklists have unchecked items. Do you want to proceed with implementation anyway? (yes/no)". Wait for the answer. "No" / "wait" / "stop" halts execution; "yes" / "proceed" / "continue" proceeds.

Note: for custom checklists, `[x]` means the reviewer judged the requirements-quality criterion satisfied — it does not mean implementation work is complete. The built-in `checklists/requirements.md` is maintained by specify and clarify.

## Execution

1. Load `tasks.md`, the spec, and the plan. Note task dependencies, IDs, file paths, and `[P]` markers.
2. **Phase by phase.** Complete each phase before moving to the next. Respect dependencies: sequential tasks run in order; `[P]` tasks may run together.
3. **Test-first within each task.** Contracts first, then tests in order contract → integration → e2e → unit, then source to make them pass. No implementation code before its tests exist and are confirmed to fail.
4. **Report progress after each completed task.** Mark each completed task `[X]` in the tasks file as you go.
5. **Halt on failure.** If a non-parallel task fails, stop — do not skip ahead. For parallel `[P]` tasks, continue with the successful ones and report the failed ones.
6. **Verify all required tasks are completed** before reporting done.

## Completion report

Final status with a summary of completed work: tasks completed/total, phases completed, any failures and how they were handled, and the next step (converge).
