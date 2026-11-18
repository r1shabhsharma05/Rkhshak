# Constraints — the quality bar, written down before the work

Distilled from the constraint-driven-development skill (MIT) and its `floor-guard.md`. Method in our own words; the full process and defaults live in that source. Use when a project needs a quality bar that survives pressure, or when agents keep quietly lowering it.

## Loading constraints
Before asking the user anything, detect what already exists: the repo's tests, linters, type checks, CI, and docs. Constraints that already exist are loaded, not re-invented. Only the gaps become questions.

## The process
1. **Detect before you ask.** Scan for existing enforcement (tests, CI, lint config). What is already enforced is already a constraint.
2. **Four questions, each with a default.** For each dimension that matters (tests, types, lint, security, performance, docs), ask the user — but always offer a sane default, so a non-answer still sets a bar. The user picks or accepts; silence accepts the default.
3. **Write CONSTRAINTS.md.** The bar lives in a file at the repo root: the floor (always enforced, no setup required), the enforced-with-numbers dimensions (thresholds), the measured-but-not-yet-enforced dimensions, and the exceptions (each with a reason and an expiry).
4. **Install what each dimension needs.** A constraint without enforcement is a wish: wire the test command, the lint rule, the CI check.
5. **Wire it to the lifecycle.** The bar is checked at the same points as the work: before commit, in CI, before merge, before launch.
6. **Guard the bar itself.** The floor guard: no change may weaken a constraint without explicit approval. A PR that lowers a threshold is a PR that changes the bar, and it says so in its title.
7. **Ratchets, when you do not have a number.** No baseline yet? Set the ratchet: the number may only improve from wherever it is today. A ratchet turns "we will measure later" into a bar that holds from day one.

## Sane defaults
Tests pass; types check; lint is clean; no secrets in the repo; no known-critical vulnerabilities in dependencies; the build is green. These are the defaults when the user does not specify otherwise — not aspirations, the floor.

## Escalation path
When a constraint cannot be met: stop, report which constraint and why, propose the smallest exception with an expiry — and wait. Quietly lowering the bar is never an option. A constraint that is impossible is a signal about the plan, not an invitation to ignore it.

## Red flags
- A dimension with no number and no ratchet.
- An exception with no expiry.
- A constraint that exists only in chat and never made it into the file.
