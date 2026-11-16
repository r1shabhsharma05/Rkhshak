# YAGNI — You Aren't Gonna Need It

YAGNI is the rule that kills speculative code: build only what is needed now. Everything else is a guess, and guesses in code become maintenance debt.

## The rule
If a feature, option, configuration, or abstraction is not needed by the current requirement, don't build it. "We might need it later" is not a requirement. "Later" almost never comes — and when it does, the requirement is different from the guess anyway.

## Where speculation hides
- **Features nobody asked for.** An admin panel, an export button, a setting — built "just in case". If no user asked for it and no requirement names it, it doesn't ship.
- **Configuration for one value.** A config file, an env var, or a settings screen for a value that has exactly one value today. Hardcode it. When the second value arrives, then make it configurable — that's a 10-minute change, not a design decision.
- **"Future-proof" code.** A plugin system, a generic framework, an interface with one implementation. Future-proofing is a bet that you know what the future needs. You don't.
- **Options and flags.** Every flag is a second code path to test, document, and maintain. One flag doubles the behaviour; three flags make eight. Add a flag only when a real user needs the choice.
- **Over-general functions.** A function that handles five cases when the caller uses one. Write the one case. Generalise when the second case arrives.
- **Dead code kept "in case".** Commented-out code, unused functions, old branches left behind. Version control is the archive. The file is not.

## The cost
Every speculative line costs three times: once to write, once to read (every future reader pays), and once to maintain (it breaks, it confuses, it blocks the change that actually matters). A codebase full of "might need" is a codebase nobody can change confidently.

## The test
Before adding anything, ask: "Is there a requirement, a user, or a test that needs this today?" If the answer is "not yet", "maybe", or "someday" — don't add it. Write the simplest thing that satisfies today's requirement, and stop.

## What YAGNI is NOT
- Not an excuse to skip tests, validation, error handling, security, or accessibility. Those are requirements, not speculation. (See the never-cut list in `references/ponytail.md`.)
- Not an excuse to write throwaway code. The code you write today should be good code — just no more of it than today needs.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Every feature/option traces to a current requirement | A feature built "just in case" |
| 2 | No config for a single value | A config file / env var / setting for one value |
| 3 | No "future-proof" frameworks or plugin systems | A generic system with one use |
| 4 | No dead code or commented-out blocks | Unused code kept "in case" |
| 5 | Flags added only for a real user choice | A flag nobody asked for |
| 6 | Security, tests, validation, a11y still present | YAGNI used as an excuse to cut a requirement |
