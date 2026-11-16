# Error Messages — clear, actionable, human

An error message is the app talking to a person who is stuck. It should say what happened, what to do next, and nothing else. Most error messages fail all three.

## The rules
- **Say what happened, in plain words.** "We couldn't save your invoice" — not "Error 500: Internal Server Error" and not "Something went wrong". The user deserves to know which thing failed.
- **Say what to do next.** Every error carries the next step: "Check your connection and try again", "Your session expired — log in again", "This email is already registered — log in or reset your password". An error with no next step is a dead end.
- **No codes, no jargon, no blame.** The user doesn't care about the error code (log it, don't show it). Never blame the user ("You entered an invalid value" → "Enter a 10-digit phone number"). The app failed to understand, not the user to be correct.
- **One error, one message.** Don't stack three errors. Show the first one, fix it, then show the next.
- **Match the tone of the product.** A banking app is calm and precise. A game is playful. An error that sounds like a legal notice in a friendly app is a tell.
- **Technical detail goes to the log.** The message the user sees is human. The stack trace, the request id, and the error code go to the log (and to support, with a reference the user can quote: "If this keeps happening, quote ref 7F3A").

## Good vs bad
| Bad | Good |
|---|---|
| `Error 500` | `We couldn't save your invoice. Try again — if it keeps failing, quote ref 7F3A.` |
| `Invalid input` | `Enter a 10-digit phone number.` |
| `Something went wrong` | `Your session expired. Log in again to continue.` |
| `You entered an invalid email` | `That email doesn't look right — check for a typo.` |
| `Failed to fetch resource` | `We couldn't load your orders. Check your connection and try again.` |

## Where errors appear
- **Inline (next to the field).** Form errors live next to the field, in text + an icon, never colour alone.
- **Toast/banner (top of screen).** For an action that failed (save, send, pay). It disappears, so it must be readable at a glance.
- **Full screen (only when nothing works).** A page that can't load gets a full-screen error with one action (retry / go home). Not a blank page.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Every error says what happened in plain words | "Error 500" or "Something went wrong" shown to the user |
| 2 | Every error carries a next step | An error with no action |
| 3 | No blame, no jargon, no codes shown | "You entered an invalid…" or a raw code |
| 4 | Form errors sit next to the field (text + icon) | Colour-only errors, or errors at the top of a long form |
| 5 | Technical detail goes to the log + a quotable ref | A stack trace shown to the user |
