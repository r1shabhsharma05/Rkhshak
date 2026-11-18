# Simplification — same behaviour, clearer code

Distilled from the code-simplification skill (MIT). Method in our own words; the full process and language notes live in that source. Use when code works but is harder to read, maintain, or extend than it should be. Size and deletion rules live in `minimal-code`; this file is about clarity.

## The five principles
1. **Preserve behaviour exactly.** Simplification changes no behaviour. Tests prove it: green before, green after, same tests.
2. **Follow project conventions.** The codebase's own idioms win over the simplifier's taste.
3. **Prefer clarity over cleverness.** A boring line a stranger understands beats a clever line that needs a comment to explain itself.
4. **Maintain balance.** Do not simplify one function by complicating its caller. The total complexity is what matters.
5. **Scope to what changed.** Simplify the code the task touches. Drive-by simplification of untouched code is scope creep.

## The process
1. **Understand before touching (Chesterton's fence).** Before removing or reshaping anything, understand why it is there. A weird line may be a workaround for a real bug; removing it reintroduces the bug.
2. **Identify opportunities.** Nested conditionals that want early returns; verbose construction that wants a literal; duplicated logic that wants one helper (only when the duplication is real — see `minimal-code` abstraction judgment); indirection that adds nothing.
3. **Apply changes incrementally.** One simplification at a time, tests green after each. A simplification that breaks a test was not a simplification.
4. **Verify the result.** Full suite green, behaviour unchanged, the diff readable on its own.

## Language notes
- **TypeScript/JavaScript:** prefer early returns over nested branches; prefer a literal or a small helper over a builder that builds the same thing; keep types honest (no `any` to "simplify" a type error).
- **Python:** prefer comprehensions and literals over verbose construction; prefer a guard clause over a nested `if`.
- **React/JSX:** prefer small components with one job over a component with many branches; lift state only as far as it is shared; do not abstract a component that is used once.

## Rationalizations — do not accept these
- "It is simpler if I rewrite the whole file" — that is a rewrite, not a simplification, and it needs its own task.
- "This clever trick saves lines" — lines saved at the cost of readability are not saved.
- "Nobody will touch this again" — somebody always does.
