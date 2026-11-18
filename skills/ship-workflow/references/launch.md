# Launch — checklist, flags, rollout, rollback

Distilled from the shipping-and-launch skill (MIT). Method in our own words; the full checklists live in that source. Use when preparing to deploy to production, or when asking what needs to be in place before shipping.

## The pre-launch checklist
- **Code quality:** tests green, review done, no dead code, no speculative features.
- **Security:** the audit gate passed (see `security-audit`); secrets rotated where needed; no secrets in the repo or the bundle.
- **Performance:** the budget holds (see `coding-craft` performance); the slowest path measured.
- **Accessibility:** keyboard, roles, names — verified, not assumed.
- **Infrastructure:** the deploy target is ready, the rollback path exists, the alerts are live with runbooks.
- **Documentation:** the README and the changelog updated in the same change.

## Feature flag strategy
Incomplete or risky features hide behind a flag; the default is the old behaviour until the new one is proven. A flag has an owner and a removal date — a flag without a removal date becomes permanent configuration.

## Staged rollout
Roll out in slices: a small percentage first, then wider, watching the same signals at each step (error rate, latency, the metrics defined in `coding-craft` observability). Each step has a decision threshold: proceed, hold, or roll back. The thresholds are written before the rollout starts, not invented mid-way.

## When to roll back
A rollback is triggered by a threshold breach (error rate, latency, a broken core flow), not by a feeling. The rollback plan names: trigger conditions, rollback steps in order, database considerations (expand/contract means the old code still works with the new schema), and time to rollback. The plan is tested before it is needed — an untested rollback is a hope.

## Monitoring and observability
What to monitor: the error rate, the latency, and the business signal the feature exists for. Error reporting goes to a tracked destination, not to a console nobody reads. Post-launch verification: run the core flows live, on the production URL, and report the result with evidence.

## Error budget release gate
Releases consume error budget; when the budget is exhausted, releases stop until reliability recovers. The budget is a number, not a mood — and it is checked before the launch, not after the incident.
