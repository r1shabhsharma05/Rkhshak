# Verify + Rollback — prove the fix, plan the way back

A fix is not done when the code is written. It is done when the failing check passes again, a regression test guards it, and the way back is planned.

## Verify the fix

### 1. Re-run the failing check
Run the exact check that found the problem, with fresh evidence. If the audit said "POST /login without a rate limit returns 200 on the 50th attempt", send 50 attempts again and watch it block. A code review is not verification — observed behaviour is.
- The check passes only on what you can observe (live probe or test output). A claim without evidence is not a PASS.

### 2. Write a regression test
Every security fix gets a test that fails without the fix and passes with it. Name it after the finding (e.g. `login-rate-limit-blocks-after-10`). The test lives in the repo, not in a chat message.
- If the fix cannot be tested (it needs a live service), write down the manual probe steps so anyone can re-run them.

### 3. Independent verification
The agent that wrote the fix never verifies its own fix. A second agent (or the user) re-runs the check with fresh evidence. This is the Verifier role — keep it separate.

### 4. Check for regressions
Run the full test suite, not just the new test. A security fix that breaks a feature is a new finding, not a fix. If the suite is red, say so and fix it — don't ship around it.

### 5. Verify on live, not just locally
Local passing is the floor. The fix must be verified against the deployed app (or the next deploy, with a note that live verification is pending). A fix verified only on localhost is marked "verified locally, live pending" — never just "verified".

## Rollback plan

### Before the change
- Know the way back: which commit to revert to, which migration to roll back, which env var to restore. Write it down in the fix report before pushing.
- If the change touches the database, the migration is reversible (or the rollback steps are written out). A migration with no way back is not shipped.

### After the change
- Watch the app after deploy: error rate, the endpoint that changed, the users it affects. If something breaks, roll back first and debug second — a broken app is worse than a delayed fix.
- A feature flag is the cleanest rollback: ship the fix behind a flag, verify, then enable it. If it breaks, flip the flag.

### If the fix was wrong
- Say so plainly. Revert, record what was wrong, and re-do it. A reverted fix is not a failure — a silently wrong fix is.

## Report format (append to the fix report)
- Finding: what it was, severity.
- Fix: what changed (files, lines).
- Verification: the re-run check + its output, the regression test name, who verified it.
- Live status: verified on live / verified locally, live pending.
- Rollback: how to undo it (commit, migration, flag).
