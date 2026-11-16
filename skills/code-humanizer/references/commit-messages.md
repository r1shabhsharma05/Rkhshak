# Commit Messages — human, lowercase, short

A commit message is the first thing a reviewer reads. It says what changed and why, in words a person would use. If it reads like a generated summary, it tells the reviewer nothing.

## The rules
- **Lowercase, human, short.** `fix login rate limit` — not `Fix: Implement Rate Limiting for Login Endpoint`. One line, under 72 characters, no jargon.
- **Imperative mood.** `fix`, `add`, `remove`, `update` — the commit does something. Not "fixed" or "fixes" or "fixing".
- **What + why, not how.** `fix login rate limit` says what. If the why isn't obvious, add one line: `fix login rate limit — brute force was possible`. The how lives in the diff, not the message.
- **One change, one commit.** A commit that does two things gets two commits. A message that needs "and" is two messages.
- **No generated filler.** No "This commit implements…", no "In this change, we…", no bullet list of files changed (the diff shows that), no ticket number as the whole message.

## Good vs bad
| Bad | Good |
|---|---|
| `Fix: Implement Rate Limiting for Login Endpoint` | `fix login rate limit` |
| `Update README.md` | `update readme with new references` |
| `Add feature` | `add dark mode toggle` |
| `Fixed bug` | `fix crash on empty cart` |
| `WIP` / `stuff` / `asdf` | (don't commit this — finish the work first, or say what it is) |

## The test
Read the message out loud. Would you say it to a colleague? "Fix login rate limit" — yes. "Implement comprehensive rate limiting functionality for the authentication subsystem" — no one talks like that.

## What this is NOT
- Not a rule about lying. If AI wrote the code, the message doesn't claim a human did. The message describes the change, not the author.
- Not a reason to skip the body. A complex change gets a body: what, why, and what to watch. The subject stays short; the body carries the context.
