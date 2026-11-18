---
name: ship-workflow
description: "Take work from idea to production safely — shape the idea, plan it into verifiable slices, set the quality bar in writing, execute with or without parallel agents, keep scope honest, and launch with a rollback plan. Use when planning any feature, running parallel work, shipping to production, setting up CI/CD, working with git branches and worktrees, or contributing to open source."
---

# Ship Workflow — from idea to production, without surprises

## Purpose
Most shipping failures are not coding failures: the idea was never shaped, the plan was never written, the quality bar was never agreed, the scope grew silently, or the launch had no way back. This skill is the workflow around the code: shape, plan, constrain, execute, review, launch, roll back if needed.

Use it when planning a feature, breaking work into tasks, dispatching parallel agents, executing a plan, setting the quality bar, reviewing a design adversarially, keeping a change in scope, finishing a branch, setting up CI/CD, launching, or contributing to open source.

## How it works (any user, any project, any stack)
No setup. No config. The agent reads this skill and the references, then runs the workflow below. It composes with `spec-kit` (spec-first: constitution → specify → clarify → plan → tasks → implement) — this skill is the execution and shipping discipline around that spec — and with `coding-craft` (the code itself) and `codebase-intelligence` (understanding before acting).

## Workflow
1. **Shape the idea.** Brainstorm, refine, and echo the ramble before any plan exists — see `references/shape-the-idea.md`.
2. **Plan it.** Dependency graph, vertical slices, tasks with checkpoints — see `references/planning.md`.
3. **Set the bar in writing.** Constraints with numbers, floors, and ratchets — see `references/constraints.md`.
4. **Challenge it.** Fresh-context adversarial review before the plan stands — see `references/adversarial-review.md`.
5. **Execute.** One task at a time, with the completion contract — see `references/executing.md`. Parallel work goes through `references/dispatching.md`.
6. **Keep it in scope.** Thin slices, scope checks on every diff — see `references/incremental.md`.
7. **Land it.** Git workflow, worktrees, finishing a branch — see `references/git-workflow.md`. CI gates it — see `references/ci-cd.md`. Open-source work follows `references/oss-prs.md`.
8. **Launch it.** Checklist, flags, staged rollout, rollback — see `references/launch.md`. Platform specifics: `references/vercel.md`, `references/platform-ship.md`.

## References
| File | What it covers |
|---|---|
| `references/shape-the-idea.md` | Brainstorming, idea refinement, thinking-out-loud echo |
| `references/planning.md` | Plan mode, dependency graph, vertical slices, tasks, checkpoints |
| `references/constraints.md` | Written quality bar — floors, numbers, ratchets, guarding the bar |
| `references/adversarial-review.md` | Doubt-driven review + fresh-context (Elephant–Goldfish) design review |
| `references/executing.md` | Executing a plan — task loop, completion contract, final review |
| `references/dispatching.md` | Dispatching parallel agents — pattern, briefs, subagent execution, ledger |
| `references/incremental.md` | Thin verifiable slices + scope-creep detection on diffs |
| `references/git-workflow.md` | Trunk-based git, atomic commits, worktrees, finishing a branch |
| `references/ci-cd.md` | Quality-gate pipeline, GitHub Actions, deploy strategies, environments |
| `references/oss-prs.md` | Open-source PR pipeline + fork PR handoff |
| `references/launch.md` | Pre-launch checklist, flags, staged rollout, rollback, error budget |
| `references/vercel.md` | Vercel cost/performance optimisation + preview environment parity |
| `references/platform-ship.md` | Shipping a Chrome extension (MV3 + store) and an Expo app (EAS + stores) |

## Rules
- **No plan, no build.** A task that feels too large to start is a task that has not been planned.
- **The bar is written before the work.** A quality bar agreed after the work is a negotiation, not a bar.
- **One task, one completion contract.** A task is done when its contract is met and verified — not when the code looks finished.
- **Parallel only when independent.** Shared state means sequential. Two agents in one file is a merge conflict, not parallelism.
- **Scope is checked on the diff, not on the intention.** A diff that grew beyond its task is split or justified, never waved through.
- **Every launch has a way back.** No rollback plan, no launch.
- **Deploy is a separate approval.** Building is not shipping; a green build is not a deploy decision. (See `security-audit` deploy authorization.)

## Provenance
Distilled in our own words from: brainstorming (MIT), idea-refine (MIT), thinking-out-loud, planning-and-task-breakdown (MIT), constraint-driven-development (MIT), doubt-driven-development (MIT), elephant-goldfish-model (Apache 2.0), executing-plans (MIT), dispatching-parallel-agents (MIT), incremental-implementation (MIT), scope-creep-detector (MIT), git-workflow-and-versioning (MIT), using-git-worktrees (MIT), finishing-a-development-branch (MIT), ci-cd-and-automation (MIT), github-actions-pro (MIT), github-oss-prs (MIT), github_fork_pr_handoff, shipping-and-launch (MIT), vercel-optimize (MIT), vercel_preview_env_parity, chrome-extensions (MIT), expo-pro (MIT). Full method and examples live in those sources.
