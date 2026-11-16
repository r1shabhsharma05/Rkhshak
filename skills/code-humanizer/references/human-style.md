# Human Style — how humans actually write code

Human code isn't sloppy. It's specific, pragmatic, and opinionated. These are the habits that make code read human.

## Comments
- **Explain WHY, not WHAT.** The code says what it does. The comment says why it does it that way.
  ```js
  // GOOD — the why isn't in the code
  // Stripe's webhook can fire twice for the same event; the idempotency
  // key is how we avoid charging twice.
  await charge({ idempotencyKey: event.id });
  ```
- **One line, not a paragraph.** If the comment needs three lines, the code probably needs a better name.
- **Only where the why isn't obvious.** Most code needs no comment. A comment on every block is a tell.
- **Real limitations, stated plainly.** `// TODO: retry on rate limit — currently fails after 3 attempts.` A human admits the edge.

## Naming
- **Domain names, not generic names.** `invoice`, `overdueCount`, `sendReminder` — not `data`, `result`, `process`.
- **Short names are fine in a small scope.** `i` in a loop, `e` in a catch, `db` for the database client. Humans don't write `indexCounter` in a for loop.
- **Abbreviations the team uses.** If the codebase says `usr`, `cfg`, `tmp`, match it. Don't "fix" local abbreviations to textbook names.
- **Names carry the decision.** `unpaidInvoices` (not `invoices`) says what the list contains. `retryAfterMs` (not `delay`) says the unit.

## Structure
- **Small functions, but not tiny.** A function does one job. If it's 3 lines and used once, inline it — a human doesn't create a function for a one-liner.
- **Some duplication is fine.** Copying 3 lines is better than a bad abstraction. Humans duplicate a little, then extract when it hurts (the third time, not the second).
- **Pragmatic trade-offs, visible.** A comment or a name that says "this is the simple version" is a human choice. Hiding the trade-off is an AI habit.
- **Uneven is normal.** A file written over months has different styles in different parts. Don't reformat a whole file to match your new code — match the part you're touching.

## Errors and edge cases
- **Validate at the boundary.** Input, API responses, user data — check them there. After that, trust the data. Don't null-check everything downstream.
- **Error messages are short and practical.** `"Card declined — try another card."` Not `"An error occurred while processing your payment. Please try again or contact support."`
- **Fail loudly.** A human doesn't swallow errors. If something unexpected happens, log it and fail — don't pretend it worked.

## What humans DON'T do
- Write a docstring for every function.
- Add a comment that restates the code.
- Create an abstraction for one use.
- Handle an edge case that can't happen.
- Use emoji in code, comments, or logs.
- Write "comprehensive", "robust", "seamless", "production-ready" in comments.
- Reformat an entire file for a 5-line change.

## The test
Read the code aloud as if explaining it to a colleague. If it sounds like a person explaining their work, it's human. If it sounds like documentation, rewrite it.
