# Logging — one list, no doubles, weekly roll-up

## The log (one list per stream)
- **One log per stream, one row per contact per channel attempt.** Columns:
  `date, contact, channel, version, status`. Status is exactly one of:
  `sent` / `delivered` / `bounced` / `replied` / `no-answer` /
  `not-interested` / `closed` / `uncontactable`. No free-text status.
- **The daily file and the log are the same list.** Every send in a daily
  file must appear as a row in the log, and every log row must trace to a
  daily file or a send record. If the two disagree, the log is wrong until
  reconciled — never the other way round.
- **Log at send time, update on outcome.** A row starts as `sent` and is
  updated to `delivered` / `bounced` / `replied` when the evidence arrives
  (bounce notice, Sent-mail check, reply). A row left as `sent` for more
  than 7 days is stale — check it and close it.

## Dedupe (no contact counted twice)
- **Check before adding:** every new contact's name and phone/email are
  checked against the full log before appending. Zero hits is the pass
  condition; a hit means the contact already exists — update the existing
  row, do not add a new one.
- **Same name, different phone is a flag, not a pass.** Two rows sharing a
  name with different phones may be two different businesses — or one
  business logged twice. Flag it in the daily file and resolve before
  either is re-contacted.
- **One entity, one row family.** A contact reached by email and then by
  text keeps one identity in the log; the channel is a column, not a new
  contact.

## Phone-vs-log comparison (the integrity check)
- Before a manual-text or call batch, compare the phone list in the daily
  file against the log: every phone must appear exactly once, and every
  phone in the batch must be absent from prior sends (unless it is a
  scheduled follow-up, which is logged as such).
- After the batch, re-count: log row count before vs after must equal the
  batch size. A mismatch means a glued row, a duplicate, or a missed row
  — find it before the next batch.

## Weekly roll-up (per stream, never blended)
Every week, publish one roll-up per stream:
- `sent / delivered / bounced / replied` since the last rewrite, plus
  reply rate (replied ÷ delivered) and bounce rate (bounced ÷ sent).
- Trigger state: distance to the next trigger (e.g. "18 sends since last
  rewrite, 12 sends to the 30-send trigger").
- Follow-ups due this week, by contact and date.
- Replies handled / still open.
- What changed since last week, in one line per change.
- The roll-up is what makes the next trigger visible *before* the next
  batch goes out. A run with no roll-up is flying blind — stop and write
  it.

## What the log must never contain
- Real contact PII copied into a shared skill or report beyond the working
  log itself. The working log lives in the user's workspace, not in this
  skill.
- A send claimed without evidence. Sent-mail verification, a bounce
  notice, or the owner's confirmation — one of the three, or it did not
  happen.
- Two different counts for the same thing. If the daily file says 10 and
  the log says 9, the report says "9 in the log, 1 unaccounted for" until
  it is found. Never round the discrepancy away.
