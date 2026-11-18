# Test-Driven Development — red, green, refactor

Distilled from the test-driven-development skill (MIT, including the merged superpowers TDD rules). Method in our own words; the full cycle and examples live in that source. Use when implementing any logic, fixing any bug, or changing any behaviour.

## Discover the stack first
The cycle is universal; the commands are not. Before the first test, find how *this* repo tests — its runner, its commands, its conventions — and use those commands for every red, green, and verification step.

## The cycle
1. **RED — write a failing test.** Write the test first. It must fail: run it and watch it fail. A test that passes immediately proves nothing. For a bug fix, the test reproduces the bug before any fix is attempted (the prove-it pattern).
2. **GREEN — make it pass.** Write the minimum code that makes the test pass. Do not over-engineer; do not add the next feature while you are here.
3. **REFACTOR — clean up.** With tests green, improve the code without changing behaviour: remove duplication, clarify names, shrink. Re-run the tests after every refactor step.

## The test pyramid
Most tests small and fast (unit), fewer integration tests, fewest end-to-end tests. Classify by resources consumed, not just by level: a test that needs a network or a database is expensive no matter what it is called. The decision guide: if it is slow or flaky, push it down the pyramid or delete it.

## Writing good tests
- **Test state, not interactions.** Assert on the outcome of an operation, not on which methods were called internally. Tests that verify call sequences break on refactor even when behaviour is unchanged.
- **DAMP over DRY in tests.** Tests read like specifications: descriptive and meaningful phrases beat shared helpers. A little duplication in tests is fine.
- **Prefer real implementations over mocks.** Use the simplest test double that gets the job done; the more real code a test exercises, the more confidence it gives.
- **Arrange-Act-Assert.** Setup, one action, assertions. One assertion per concept; name tests descriptively, so the test name states the behaviour.

## Anti-patterns
Testing implementation details; mocking the thing under test; a test that cannot fail; slow suites nobody runs; tests that depend on run order; asserting on incidental output.

## Iron law
Never skip the red run. Never skip the green run. "Seems right" is not done — the test output is the proof. Exceptions (a spike, a throwaway probe) need explicit approval, and the code does not ship until the tests exist.

## Rationalizations — do not accept these
- "The change is too small to test" — small changes break things too; the test is the proof.
- "I will add tests later" — later never comes; the test comes first or not at all.
- "The manual check passed" — a manual check is not a regression test.
