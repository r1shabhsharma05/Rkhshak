# Test Naming — readable tests that document behaviour

A test name is the documentation of what the code does. When a test fails, its name is the first thing anyone reads. If the name doesn't say what broke, the test is noise.

## The rules
- **A test name says what it checks, in plain words.** `login blocks after 10 wrong passwords` — not `testLogin1`, `test_login`, or `shouldWork`. The name is a sentence about behaviour.
- **Name the behaviour, not the method.** `sends an SMS to guardians on SOS` beats `testSendSms`. The method name is in the code; the test name says what the user gets.
- **Include the condition.** `returns 404 for a deleted invoice`, `allows the owner but not a stranger`, `retries once then fails`. The condition is what makes the test meaningful — without it, the test could be checking anything.
- **No test numbering.** `test1`, `test2`, `test3` say nothing. If two tests need numbers to tell them apart, their names are wrong.
- **One behaviour per test.** A test that checks three things has three names fighting for one slot. Split it. When it fails, you should know exactly which behaviour broke.
- **Failure messages read like sentences.** When a test fails, the output should read: "login blocks after 10 wrong passwords — expected 429, got 200". If the output is `AssertionError at line 42`, the test name didn't do its job.
- **Test files mirror the code.** A test for `auth.js` lives in `auth.test.js`, next to it. A reader finds the test for a file without searching.

## Good vs bad
| Bad | Good |
|---|---|
| `testLogin1` | `login blocks after 10 wrong passwords` |
| `test_send_sms` | `sends an SMS to guardians on SOS` |
| `shouldWork` | `returns the user's own invoices, not others'` |
| `testEdgeCase` | `rejects a token with alg none` |
| `test1, test2, test3` | (each test named for its behaviour) |

## Test style (the human part)
- **Arrange, act, assert — visible.** Setup, the call, the check — in that order, with a blank line between them. A reader sees the shape before reading the lines.
- **No magic in setup.** A helper that builds test data is named for what it builds (`aLoggedInUser()`, `anUnpaidInvoice()`), not `setup()` or `data()`.
- **Real values, not placeholders.** `alex@example.com` beats `test@test.com`. A real-looking value is easier to read and harder to confuse with a placeholder.
- **Delete the test that tests nothing.** A test with no assertion, or one that passes no matter what the code does, is worse than no test — it claims coverage that doesn't exist.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Every test name is a sentence about behaviour | `test1`, `shouldWork`, `testLogin` |
| 2 | The condition is in the name | A name with no condition (`returns invoices`) |
| 3 | One behaviour per test | A test checking three things |
| 4 | Failure output reads like a sentence | `AssertionError at line 42` with no behaviour named |
| 5 | Test files mirror the code files | A test that can't be found from the file it tests |
| 6 | No assertion-less tests | A test that passes no matter what |
