# Regression Tracking — compare audit runs over time

A single audit is a snapshot. A skill that tracks regressions is useful over time. Compare every new run against the previous run and report what changed.

## How it works
1. **Keep every AUDIT.md.** Store each run's AUDIT.md (with its date, commit, and counts) in the repo or a runs folder. Never overwrite the previous run.
2. **Carry forward open findings.** Every finding that was open in the previous run stays open in the new run unless fresh evidence shows it fixed. A fix claim without fresh evidence does not close a finding.
3. **Classify each finding in the new run:**
   - **New** — not in the previous run (new code, new check, or newly discovered).
   - **Fixed** — was open, now passes with fresh evidence (test output or live probe).
   - **Regressed** — was passing, now fails (a change broke it).
   - **Still open** — was open, still open.
   - **Risk-accepted** — was open, user accepted the risk in writing (record reason + expiry).
4. **Report the delta first.** The new run's report opens with the delta: X new, Y fixed, Z regressed, W still open. A regression is a Critical-priority item — it means a fix or feature broke a previously passing control.
5. **Never claim "all fixed" without a full re-run.** A fix round fixes listed findings; only a full re-run of every check proves the gate. A partial re-run (only the fixed checks) is not a gate pass.

## What to store per run
- Date, commit/branch, live URL probed.
- Counts: Passed · Fixed · Still open · Needs human · N/A · Can't verify.
- The finding list with severity + status (new / fixed / regressed / still open / risk-accepted).
- The delta vs the previous run.

## When to compare
- Every run, automatically. If no previous run exists, say so in the report — never imply a first run is a regression-free run.
