# Dispatching Parallel Agents — independent work, in parallel, integrated once

Distilled from the dispatching-parallel-agents skill (MIT). Method in our own words; the full pattern and examples live in that source. Use when facing two or more independent tasks with no shared state or sequential dependencies, or when executing an implementation plan with fresh subagents per task.

## The pattern
1. **Identify independent domains.** The tasks must not share state, files, or ordering. Shared state means sequential — two agents in one file is a merge conflict, not parallelism.
2. **Create focused agent tasks.** Each task is self-contained: the goal, the files, the constraints, the verification, and the report format. A task that needs a conversation is not a dispatchable task.
3. **Dispatch in parallel.** All agents run concurrently, each in its own context. They do not talk to each other; the dispatcher integrates.
4. **Review and integrate.** Read every report, verify the claims (see `coding-craft` verification), resolve conflicts, and integrate in dependency order. Integration is the dispatcher's job, never the agents'.

## Agent prompt structure
Every brief carries: the task (one thing), the scope (files and boundaries), the constraints (the quality bar, the rules that apply), the verification (what to run, what output proves it), and the report format (what changed, what was verified and how, what is still open). Nothing else — a brief with a persuasion paragraph is a brief with a bias.

## Common mistakes
- Dispatching dependent tasks in parallel and discovering the dependency mid-flight.
- A brief without a verification step, so the agent reports "done" with no proof.
- Integrating without reviewing — the dispatcher's review is the quality gate, not a formality.
- Too many agents: each agent costs context and coordination. Parallelism pays only when the tasks are genuinely independent and genuinely large.

## When NOT to use
- The tasks share files or state.
- The task needs a conversation or a judgment call mid-way.
- The work is small enough that dispatching costs more than doing it.

## Subagent-driven plan execution
For executing a whole plan with subagents: set up a worktree, a ledger (which task is in which state), and a pre-flight scan (environment, branch, baseline tests green) first. Then the task loop: dispatch the implementer for one task → handle the report (verify the claims) → review the task (against its contract) → run the fix loop if it fails (same agent, bounded rounds) → complete the task (record it in the ledger) → next task. Final review covers the whole change; finish with the per-task report. Rulings, not stalls: when an agent is blocked, the dispatcher rules (redirect, split, or stop) — the plan does not wait silently.
