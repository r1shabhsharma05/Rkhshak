# Abstraction Judgment (AHA) — when NOT to abstract

The most expensive code is not the code you wrote. It's the abstraction you built too early, that every later change has to fight. AHA — Avoid Hasty Abstractions — is the rule: don't abstract until the duplication has proven itself.

## The rule of three
- First use: write it inline. No function, no helper, no shared module.
- Second use: copy it. Duplication is cheaper than a wrong abstraction. Two copies that do slightly different things are honest; one abstraction that pretends they're the same is a lie.
- Third use: now abstract — and only now, when you can see what is actually common and what is actually different.

## When to abstract
- The same change has to be made in three or more places, and the change is the same every time.
- The abstraction has a clear name that says what it is (`sendTemplatedEmail`, not `processData`).
- The abstraction is simpler to understand than the code it replaces. If a reader has to understand the abstraction AND the three call sites to follow one flow, it made things worse.

## When NOT to abstract
- **Different reasons to change.** Two pieces of code look alike today but change for different reasons (one changes when the pricing changes, the other when the email template changes). Abstracting them couples two things that should move independently. The next change breaks one of them.
- **Only two uses.** Two is a coincidence, not a pattern. Wait for the third.
- **The abstraction needs configuration to handle the differences.** If the shared function takes five flags to cover two cases, it's not an abstraction — it's two functions wearing a trench coat. Keep them separate.
- **You're guessing at the future.** "We might need this for other types later" is speculation. Build for the case you have. When the second case arrives, then decide.
- **The name is vague.** If you can't name it without `utils`, `helpers`, `common`, `Manager`, or `Service`, you don't know what it is yet. Don't abstract what you can't name.

## The cost of a wrong abstraction
A wrong abstraction is harder to remove than duplication is to live with. Every caller depends on it, every change has to go through it, and untangling it means touching everything at once. Duplication is visible and local; a bad abstraction is invisible and everywhere.

## The test
Before abstracting, ask: "If these two uses diverge tomorrow, will I regret coupling them?" If the answer is yes — or "I don't know" — don't abstract yet. Wait for the third use. The code will tell you when it's ready.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Abstraction appears at the third use, not the first | A helper built for a single use case |
| 2 | Abstracted pieces change for the same reason | Two things coupled that change independently |
| 3 | The abstraction has a clear, specific name | `utils`, `helpers`, `Manager`, `processData` |
| 4 | No configuration flags papering over differences | A shared function with 5 flags for 2 cases |
| 5 | The abstraction is simpler than what it replaced | A reader must understand the abstraction + all call sites to follow one flow |
| 6 | No speculative abstraction ("might need later") | An abstraction built for a case that doesn't exist yet |
