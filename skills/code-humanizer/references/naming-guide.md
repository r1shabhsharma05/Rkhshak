# Naming Guide — human variable, function, and component names

A name is the first documentation. If a reader can't tell what a thing is from its name, the code is already hard to read — no matter how clean the logic is.

## Rules
- **A name says what it IS or what it DOES.** `unpaidInvoices`, `sendReminder`, `isEligible` — the reader knows without reading the body. `data`, `result`, `temp`, `handleClick`, `doStuff` say nothing.
- **Domain language, not programmer language.** Name things the way the product talks about them: `invoice`, `guardian`, `sosAlert` — not `item`, `entity`, `obj`, `record`. If the user calls it an "invoice", the code calls it an `invoice`.
- **Booleans read like a question.** `isActive`, `hasPermission`, `canEdit`, `shouldRetry`. Never a bare adjective (`active`) or a noun (`permission`) for a boolean.
- **Functions are verbs.** `sendEmail`, `calculateTotal`, `validateAddress`. A function named with a noun (`email`, `total`) hides what it does.
- **No generic names in a real scope.** `data`, `info`, `value`, `item`, `result`, `temp`, `x` are fine as a loop variable or a throwaway. As a function parameter, a return value, or a module-level name, they are a smell — the author didn't know what the thing was, or didn't care.
- **Avoid AI-generated name patterns.** `handleX` for every handler (name what happens: `onSave` → `saveInvoice`), `getX`/`fetchX`/`processX` for everything, `utils`/`helpers`/`common` as a dumping ground, `Manager`/`Handler`/`Service` suffixes that mean nothing. If a name could belong to any function in any project, it's not a name.
- **Length fits the scope.** A loop counter is `i`. A module-level function gets a full name. A name used across the codebase earns its length; a name used in three lines doesn't need it.
- **Consistent conventions.** One project, one convention: `camelCase` or `snake_case`, `is/has/can` for booleans, the same word for the same concept everywhere (`user` is always `user`, never `account` in one file and `profile` in another).
- **Rename when the meaning changes.** If a function starts doing something else, its name changes in the same commit. A stale name is a lie that every future reader believes.
- **Abbreviations are a debt.** `usr`, `addr`, `qty`, `cfg` save 2 characters and cost every reader a pause. Spell it out unless the abbreviation is universal in the domain (`id`, `url`, `api`).

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Every name says what the thing is or does | A `data`, `result`, `temp`, or `doStuff` in a real scope |
| 2 | Domain language, not programmer language | `item`/`entity`/`obj` where the product has a real word |
| 3 | Booleans read like questions (`is/has/can`) | A boolean named with a noun or bare adjective |
| 4 | Functions are verbs | A function named with a noun |
| 5 | No `utils`/`helpers`/`Manager` dumping grounds | A file or class that holds unrelated things under a generic name |
| 6 | Same concept, same word everywhere | `user` in one file, `account` in another, same thing |
| 7 | Names updated when meaning changed | A function whose name describes what it used to do |
