# Delete First — remove before adding

Every change starts by deleting. Code that doesn't exist can't break, can't be read wrong, and costs nothing to maintain.

## What to delete
- **Dead code.** Functions, variables, branches, and imports nothing calls. If nothing references it, delete it. (Check first: search the codebase, don't guess.)
- **Commented-out code.** Old code in comments is not history — version control is history. Delete it.
- **Speculative features.** Code built for a use case nobody asked for. "We might need this later" is not a use case.
- **Duplicate logic.** The same 5 lines in two places. Extract it once — but only on the third copy, not the second. Two copies is fine; three is a pattern.
- **One-use wrappers.** A function called once that wraps a one-liner. Inline it.
- **Unnecessary config.** Options nobody changes, flags nobody flips, settings with one value. Delete the option, hardcode the value, and say so in a comment if it matters.
- **Old migrations / old code paths.** A feature flag that's been on for months, an old API version nobody calls, a deprecated endpoint. Remove the old path and the flag.

## How to delete safely
1. **Search first.** Grep for every reference to the thing you're deleting. If something still uses it, don't delete it — or update the caller first.
2. **Delete in the same change.** Don't leave the deletion for "later". Later never comes.
3. **Tests must still pass.** If a test breaks, the code wasn't dead — or the test was testing dead code (delete that too).
4. **One deletion per change is fine.** A change that only deletes is a good change. Report it as such.

## What NOT to delete
- Code with a comment explaining why it exists (a workaround, a quirk, a compliance requirement). Read the comment first.
- Code that looks unused but is called by reflection, by a framework, or by an external system (webhooks, cron jobs, migrations).
- Public API surface other people depend on. Deprecate it first, delete it in a later release.

## The rule
If you can't explain why a line exists, delete it. If you can explain it, keep it — and make sure the explanation is in a comment or a name, not just in your head.
