# Executing Plans — the task loop and the completion contract

Distilled from the executing-plans skill (MIT). Method in our own words; the full process and example live in that source. Use when executing an implementation plan in the current session as the implementer.

## Setup
Read the plan in full before touching anything. Confirm the environment (branch, worktree, dependencies installed), the task order, and the checkpoints. If the plan is ambiguous, ask — do not improvise the plan while executing it. (For plans executed by parallel agents, see `references/dispatching.md`.)

## The task loop
For each task, in order:
1. **Take the task.** State which task you are starting and what its done condition is. One task at a time; no starting the next task while this one is unverified.
2. **Work the steps.** Follow the plan's steps in order, running each step's verification as you go. If a step fails, stop and fix it — do not carry a failed step into the next one.
3. **The completion contract.** A task is complete only when: every step ran, every verification passed with its output read, the tests for the touched area pass, and the diff contains only what the task asked for. Anything less is "in progress", and is reported as such.
4. **Complete the task.** Record the completion (what changed, what was verified and how, what is still open) and move to the next task. The record is the audit trail — without it, nobody can tell what was done.

## Final review
When all tasks are done: re-read the plan's goal and check the whole change against it. Run the full verification (suite, build, and any plan-level checks). Report the outcome per task, not as a single "done".

## Finish
Hand back a report: what was done, per task, with evidence; what was verified and how; what is still open or explicitly deferred; and what the next step is. Never report a task complete that its contract does not cover.

## Common rationalizations — do not accept these
- "The task is basically done" — basically done is not done; the contract decides.
- "I will verify at the end" — verification deferred is verification skipped; verify per task.
- "The plan is outdated, I improved it as I went" — then stop, update the plan, and get it agreed. Silent plan changes are scope changes.
