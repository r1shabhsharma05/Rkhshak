# Smallest Complete Change — the discipline

"Smallest" and "complete" pull in opposite directions. The skill is holding both at once.

## The smallest complete change
- **Smallest:** the fewest lines, the fewest files, the fewest new concepts. One job, one place.
- **Complete:** the task is fully solved — the feature works, the bug is fixed, the tests pass, the docs are updated if they need to be. Not half done, not "mostly".
- A change that is small but incomplete is a draft. A change that is complete but bloated is a liability.

## How to find it
1. **Say the change in one sentence.** "Add a rate limit of 30 requests per 15 minutes on the SOS endpoint." If you can't say it in one sentence, you don't understand the task yet.
2. **List the files the change must touch.** If the list is long, the change is probably two changes. Split it.
3. **Write the test first (or the check).** Know how you'll prove it works before writing the code. The test defines "complete".
4. **Write the code.** No extra features, no refactoring of nearby code, no "while I'm here" improvements. The change does one thing.
5. **Re-read the diff.** Every line in the diff must be necessary. If a line doesn't serve the one-sentence change, remove it.

## Library first (never hand-build what exists)
- Need a date? Use the platform's date library, not a hand-rolled parser.
- Need a UI component? Use the installed component library, not a custom one.
- Need auth? Use the auth provider, not a hand-rolled session.
- Need a queue? Use the queue service, not a setTimeout loop.
- If the library does 90% of what you need, use the library and write the 10%. Don't build 100% because the library "isn't perfect".

## When minimal is wrong
- **Readability beats brevity.** A clear variable name is worth a line. A comment explaining WHY is worth a line. Don't golf.
- **Don't over-extract.** A helper used once is not a helper — it's an indirection. Inline it.
- **Don't over-inline.** If the same logic appears three times, extract it. Two times is fine.
- **Security and correctness are never "extra".** Validation, auth checks, error handling — these are part of "complete", not bloat. Never cut them to make the diff smaller.

## The test
Show the diff to a colleague. If they can understand the whole change in 30 seconds, it's small enough. If they need 5 minutes, it's too big — split it.
