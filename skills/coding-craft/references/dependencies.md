# Dependencies and Deprecation — add carefully, remove deliberately

Distilled from two sources, in our own words: dependency-doctor (MIT) and its `dependency-pitfalls.md`, and deprecation-and-migration (MIT). Full procedures live in those sources. Use when adding or auditing a dependency, or when removing an old system, API, or feature.

## Dependency diagnosis (offline, before installing)
Choose the manifest first (`package.json`, `pyproject.toml`, `requirements.txt` — the one this repo actually uses), then check the direct dependencies for surface-level footguns:
- **Standard-library shadowing pins** — a dependency whose name collides with a standard-library module.
- **Abandoned packages** — no release, no maintainer activity, open critical issues with no response.
- **Yanked or unresolvable versions** — a pinned version the registry no longer serves (check the registry; do not guess).
- **Duplicate jobs** — two packages doing the same thing; one must go (`minimal-code` dependency diet applies).
Explain the diagnosis in plain terms, offer fixes, and never apply them silently — the user approves each change.

## Code is a liability
Every line, every dependency, every endpoint is something to maintain. Removal is a feature. Deprecation planning starts at design time: anything public will one day need removing, so design the exit when you design the entrance.

## Hyrum's law makes removal hard
Once users depend on observable behaviour, removing it breaks them — even behaviour you never documented. Measure usage before removing anything; "nobody uses this" is a claim that needs evidence.

## The deprecation decision
- **Compulsory deprecation:** the old system must go (security, cost, correctness). A deadline exists, and the migration is tracked to completion.
- **Advisory deprecation:** the old system is discouraged but works. No deadline, but no new users and no new features on it.

## The migration process
1. **Build the replacement.** It must be complete and verified before anyone is asked to move.
2. **Announce and document.** A deprecation notice (what, why, when, what replaces it) plus a migration guide with before/after examples.
3. **Migrate incrementally.** Move users in slices, highest-value first, verifying each slice. Never a big-bang migration.
4. **Remove the old system.** Only after usage is zero (measured, not assumed) and the removal is verified. Dead code left behind becomes zombie code: it looks alive, nobody owns it, and it confuses every reader. Delete it.

## Migration patterns
- **Strangler pattern:** the new system gradually takes over routes or calls from the old one until nothing is left.
- **Adapter pattern:** a shim lets old callers use the new implementation during the transition — then the shim is deleted too.
- **Feature-flag migration:** the new path rolls out behind a flag, slice by slice, with instant rollback.
- **Database schema (expand/contract):** expand (add the new shape, write both), migrate the data, contract (remove the old shape). Never a single-step schema change on live data.

## Verification
The replacement is verified by its own tests; the migration is verified by usage metrics hitting zero on the old path; the removal is verified by the suite passing with the old code gone.
