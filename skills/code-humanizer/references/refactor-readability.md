# Refactor for Readability — restructure AI code so it reads human

AI-generated code usually works. It rarely reads like a person wrote it: flat structure, generic names, defensive bloat, no point of view. Refactoring for readability is not beautifying — it's making the code understandable to the next person.

## The moves (in order)
### 1. Extract functions with intent-revealing names
A 40-line function that does three things becomes three functions, each named for what it does. The top function reads like a summary; the details live below. If you can't name the extracted piece, you don't understand it yet — that's the signal to read it again, not to leave it inline.

### 2. Flatten nesting with early returns
```
# BEFORE: nested, hard to follow
if user:
    if user.is_active:
        if user.has_permission:
            do_the_thing()

# AFTER: flat, the happy path is obvious
if not user: return
if not user.is_active: return
if not user.has_permission: return
do_the_thing()
```
Guard clauses first, happy path last. A reader should see the normal flow without tracking three levels of `if`.

### 3. Remove dead code
Commented-out blocks, unused functions, unreachable branches, imports nothing uses. AI code accumulates these because the model hedges. Delete them. Version control remembers; the file doesn't need to.

### 4. Group related code
Things that change together live together. A validation and the error it produces sit next to each other, not in two files. If a reader has to jump between three places to understand one behaviour, the code is organised by accident, not by intent.

### 5. Comments explain WHY, not WHAT
Delete comments that restate the code (`// increment i`). Keep (or add) comments where the why isn't obvious: a business rule, a workaround with a reason, a decision that looks wrong but isn't. One honest "why" comment is worth ten "what" comments.

### 6. Replace magic numbers with named constants
`if (attempts > 3)` → `const MAX_LOGIN_ATTEMPTS = 3`. The name carries the meaning; the number alone doesn't. Same for strings that carry meaning (`"admin"` → `ROLE_ADMIN`).

### 7. Break long functions
A function longer than a screen is doing more than one thing. Split it. The split point is where you would start a new sentence if you were explaining it.

### 8. Consistent structure
One file, one shape: imports, constants, helpers, main export — in the same order every time. A reader who knows the shape of one file knows the shape of all of them.

## What NOT to do
- Don't refactor for cleverness. A shorter line that takes longer to understand is worse.
- Don't rename everything at once. Rename the thing you're touching, in the same change, with a test proving nothing broke.
- Don't restructure working code without a reason. "It reads badly" is a reason. "I prefer it another way" is not.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Every function does one thing, named for it | A 40-line function doing three things |
| 2 | Nesting flattened with early returns | Three levels of `if` around the happy path |
| 3 | No dead code, no commented-out blocks | Unused functions or commented code left in |
| 4 | Related code lives together | One behaviour split across three files for no reason |
| 5 | Comments explain WHY only | Comments restating what the code does |
| 6 | Magic numbers/strings named | A bare `3` or `"admin"` carrying meaning |
| 7 | One consistent file shape | Every file organised differently |
