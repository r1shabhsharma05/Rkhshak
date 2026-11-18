# Diagnose zero replies — four causes, evidence per cause

A 0-reply run is a symptom, not a diagnosis. Never rewrite the template
until the cause is named, and never name a cause without its evidence.
Work the four causes in this order — cheapest to rule out first.

## The four causes

### 1. Deliverability — the mail never arrived
Evidence to collect:
- Bounce count and bounce codes from the inbox (e.g. `550 5.1.1`
  mailbox does not exist = hard bounce; `550` / spam-filter rejections).
  A bounce rate above ~10% of sends means the address list, not the
  copy, is the problem.
- Sent-mail verification: every claimed send must appear in Sent mail.
  A send with no Sent-mail record did not happen — count it as unsent.
- Sender state: is the sending account still connected and authenticated?
  A stale password or a revoked connection silently kills a whole run;
  reconnecting is owner-only, never the agent's job to guess credentials.
- Spam placement: no opens, no clicks, no bounces, no replies across a
  whole batch points at the spam folder or a reputation problem, not at
  the wording.

Rule-out test: if most mail was delivered (no bounce, in Sent mail) and
still 0 replies, deliverability is not the main cause — move on.

### 2. Targeting — the wrong person or company
Evidence to collect:
- Role check: is the recipient the person who can say yes? A founder or
  engineering leader can; a generic inbox or a wrong department cannot.
- Fit check: does this company actually need what is offered, right now?
  A hiring post, a missing website, a dated public signal — or nothing?
  Contacts with no cited pain are speculative-fit, not qualified.
- Address check: was the address published, stated by the person, or
  guessed from a pattern? Guessed addresses that bounce in bulk mean the
  targeting step failed before the copy was ever read.

Rule-out test: if recipients are verified decision-makers with a real,
cited need and the mail was delivered, targeting is not the main cause.

### 3. Offer — the value is unclear
Evidence to collect:
- Read the sent template as the recipient would: can they say in one
  sentence what they get and what it costs them? If not, the offer is
  the problem.
- Is the ask proportionate? A 10-minute call is a small ask; a demo, a
  trial, or a decision is not. A big ask in email one kills replies.
- Is there a concrete next step, or only "let me know"? A reply needs
  something to say yes to.

Rule-out test: if three strangers can state the offer back after one
read, the offer is clear enough — move on to copy.

### 4. Copy — the template fails
Evidence to collect:
- Length: over ~120 words for a first cold email is long. Cut, don't add.
- Personalisation: is there one named, researched fact about this lead —
  or generic flattery ("impressive company")? Flattery is not
  personalisation.
- Subject line: does it name the lead or their problem, or is it clever
  for its own sake? Clever subjects get opened and ignored.
- Version history: which version did each contact get? If versions were
  mixed silently, no conclusion about any version is valid.

## Rewrite triggers (hard numbers — do not negotiate these mid-run)
- **30 sends / 0 replies = STOP.** No further sends of that template.
  Diagnose (above), then propose a rewrite to the owner. Sending resumes
  only after the owner approves the new template.
- **15 sends / 0 replies = WARNING.** Keep sending only the already
  approved batch; start the diagnosis in parallel so the rewrite is ready
  at 30.
- **Bounce rate > 10% = STOP the list, not the template.** Pause sends,
  re-verify the remaining addresses, drop hard bounces. The copy is
  innocent until the list is clean.
- **Follow-ups also at 0 replies do not reset the trigger.** A follow-up
  is the same template family. The count is sends, not batches.

## Diagnosis report (write this before any rewrite)
- Stream, sends / delivered / bounced / replied since last rewrite.
- Cause ranked 1–4 with the evidence for each (bounce codes, Sent-mail
  check, role/fit sample, offer read-back, copy check).
- What was ruled out, and what evidence ruled it out.
- Proposed change: exactly one variable (see `email-copy.md` — A/B
  discipline), and what would prove it worked.
- Owner decision needed: approve the rewrite, change the target list, or
  pause the stream.
