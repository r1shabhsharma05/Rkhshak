# Dependency Fix — upgrade, patch, fork, or replace

A dependency has a known vulnerability. Four options, in order of preference. Pick the first one that works — don't jump to the hardest one.

## The options (in order)
### 1. Upgrade (first choice)
- Update to the fixed version. Check the changelog: what changed, what breaks.
- Run the test suite. If green, ship it. This is the fix 90% of the time.
- If the fixed version needs a major bump (breaking changes), estimate the migration cost before deciding — but don't use "it's a major version" as a reason to stay vulnerable.

### 2. Patch (when upgrade isn't possible yet)
- Apply the upstream patch (or a community patch) to the current version. Use a patching tool (`patch-package` for npm) so the patch is recorded in the repo, not a silent edit in `node_modules`.
- The patch is temporary: record which version it applies to and when it should be removed (the next upgrade that includes the fix).

### 3. Fork (when upstream is dead)
- If the package is unmaintained and no fix exists, fork it, fix it, and point the dependency at the fork.
- A fork is a commitment: the team now owns that code. Say so in the record. Don't fork silently — the next person needs to know why the dependency points at a fork.

### 4. Replace (when the dependency isn't worth it)
- If the package is small, unmaintained, or does something the stdlib already does — remove it and replace it with the stdlib, or with a maintained alternative.
- The best dependency fix is often deleting the dependency. (See `minimal-code`: delete-first.)

## The decision (ask these in order)
1. Is there a fixed version? → Upgrade.
2. Is there a patch? → Patch (temporarily).
3. Is upstream alive? → Wait for the fix + contain the risk (or patch).
4. Is upstream dead? → Fork or replace.
5. Is the dependency worth keeping at all? → Replace or delete.

## Contain while you decide
- If the vulnerability is exploitable and the fix will take time, contain it: block the affected endpoint, disable the feature that uses the package, or add a WAF rule.
- Containment is not a fix. The fix still ships.

## The record (one per vulnerable dependency)
- Package, version, vulnerability (CVE/Advisory id), severity.
- Option chosen + why (and why the earlier options didn't work).
- If patched: the patch file + which version removes it.
- If forked: the fork URL + who owns it.
- Verification: the audit is clean (or the finding is risk-accepted in writing with an expiry date).

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Fixed version installed, tests green | Still on the vulnerable version with a fix available |
| 2 | Patch recorded in the repo (not a silent edit) | A patched `node_modules` with no record |
| 3 | Fork documented with an owner | A fork nobody knows about or owns |
| 4 | Unneeded dependency removed, not kept | A vulnerable package kept "just in case" |
| 5 | Risk-acceptance (if any) in writing with an expiry | An open vulnerability with no record and no date |
