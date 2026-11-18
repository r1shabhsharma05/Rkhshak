# Deliverability — verify before send, bounce honestly

## Verification is a screen, not proof
- An email check can say: syntax valid, domain exists, MX records
  present, not a disposable domain, not a typo of a major provider.
  Verdicts: `invalid` | `typo` | `role-account` | `disposable` |
  `domain-ok`. Only `domain-ok` proceeds — and `domain-ok` means the
  domain accepts mail. **That is all it means.**
- **A verification score does not guarantee delivery.** This is a recorded
  failure, not a theory: addresses scored deliverable (up to 97/100) by a
  third-party checker later bounced in Gmail with a 550 — 8 such false
  positives in one run. A high score is a green light to attempt a send,
  never a claim the mailbox exists.
- Catch-all domains are unconfirmable by verification alone: a "deliverable"
  verdict on a catch-all domain proves nothing about the mailbox. Send
  flagged, or skip.
- Role accounts (`info@`, `admin@`, `support@`) are not cold-email targets.
  Skip them.
- Direct SMTP mailbox checks are often impossible from a sandboxed host
  (outbound port 25 blocked at egress). Do not burn a run debugging SMTP;
  use a checker as a pre-filter and let the real send be the test.

## Guessed addresses
- An address built from a name pattern (`first@`, `first.last@`,
  `flast@`) is labelled `guess` — never `verified`, never presented as
  confirmed. Verify-first, then send.
- A guess that bounces is a dead address, not a deliverability mystery.
  Log it and move on; do not try a second guess for the same person in
  the same batch unless the owner asks for it.
- Never send to a typo'd address. Fix the typo first.

## Bounce handling (hard rules)
- **Hard bounce (`550 5.1.1` mailbox does not exist, or any permanent
  failure) = stop that address.** Log it, mark the contact dead for that
  address, move on. Never re-send to a bounced address.
- **Soft bounce (mailbox full, temporary rejection) = one retry only,**
  after at least 24 hours. A second soft bounce becomes a hard stop.
- Count bounces in the roll-up. A bounce rate above ~10% stops the list
  (see `diagnose-zero-replies.md`) — the list is the problem, not the copy.
- Every bounce must be matched to its send in the log. An unmatched
  bounce means the log is wrong; fix the log before the next batch.

## Sender reputation (what the agent can and cannot do)
- Send from one consistent, authenticated sender account, in the
  approved send window (e.g. morning local time). No BCC blasts, no
  links-and-attachments bundles, no sudden volume spikes.
- Keep volume low and steady: small daily batches, not one big blast.
  A new sender account warms up over days, not hours.
- If the sender account's saved password goes stale (the owner changed
  it), sends stop. Reconnecting is owner-only — the agent never guesses
  credentials, never retries a stale login, and says plainly that sends
  are blocked until the owner reconnects.
- Verify every send in Sent mail the same day. A claimed send with no
  Sent-mail record is unsent — correct the log, do not defend the count.

## The standing example (keep this in the skill)
A checker scored an address 97/100 deliverable; Gmail then bounced it
with a 550. That is the standing proof that verification ≠ delivery, and
the reason this skill counts delivery by bounces and Sent mail, never by
checker scores.
