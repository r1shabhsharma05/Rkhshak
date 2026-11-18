# CI/CD — the quality gate pipeline

Distilled from two sources, in our own words: ci-cd-and-automation (MIT) and github-actions-pro (MIT). Full configurations live in those sources. Use when setting up or modifying build and deployment pipelines, or when automating quality gates.

## The quality gate pipeline
Every change passes the same gates, in the same order: lint → type check → unit tests → integration tests → build → (preview deploy) → end-to-end tests. A gate that is skipped for one change is a gate that does not exist.

## GitHub Actions: design rules
- **Triggers deliberately.** `push`, `pull_request`, `workflow_dispatch`, `schedule`, `release` — each workflow names its triggers on purpose. `pull_request` from forks runs in a restricted context; `pull_request_target` checks out attacker-controlled code with base-repo permissions — understand it before using it.
- **Least-privilege tokens.** Set `permissions:` explicitly at workflow or job level; the default broad token is a supply-chain risk.
- **Pin actions.** Reference third-party actions by full commit SHA, not mutable tags; keep SHAs updated automatically.
- **Script injection.** Never interpolate untrusted input (PR titles, issue bodies) into `run:` scripts — it is code execution. Use environment variables instead.
- **Caching.** Cache dependencies and build outputs keyed on lockfiles, with restore-keys for partial hits. Do not let untrusted PRs write caches that privileged workflows read.
- **Artifacts** pass build outputs between jobs; they are for CI handoff, not long-term storage.
- **Environments.** Named environments (staging, production) with protection rules: required reviewers, wait timers, branch restrictions.
- **Reusable workflows and composite actions** are the DRY mechanism for repeated CI — inputs and secrets typed explicitly.
- **OIDC to clouds** instead of stored secrets wherever the cloud supports it.
- **Concurrency groups** cancel superseded runs (PR pushes) so obsolete commits stop wasting minutes.

## Feeding CI failures back to agents
A CI failure is a task: read the failing log, reproduce it locally where possible, fix the cause (not the log line), and re-run the same gate. A fix that passes locally but fails in CI was not reproduced — read the CI environment, not just the code.

## Deployment strategies
- **Preview deployments** on PRs (the deploy target's preview flow) so the change is verified where it will run.
- **Feature flags** for incomplete or risky features.
- **Staged rollouts** with a rollback plan (see `references/launch.md`).
- **Environment management:** one source of truth per environment; secrets via the platform's secret store, never in the repo or the workflow file.

## Automation beyond CI
Dependabot or Renovate for dependency updates (including pinned action SHAs); a build-cop role when the pipeline is busy; PR checks that block merge on red gates. CI optimisation: cache first, parallelize second, split the slowest job third — measure the minutes before optimising them.
