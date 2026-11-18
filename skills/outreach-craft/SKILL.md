---
name: outreach-craft
description: "Write, send, follow up, and diagnose cold outreach that gets replies — email, WhatsApp, and calls — with hard rewrite triggers, deliverability checks, and a log that makes the next decision visible. Use when replies are zero, a template needs rewriting, a follow-up is due, a reply lands, or a new outreach run is being planned. Lead-gen finds leads; this skill works them."
---

# Outreach Craft — diagnose first, write short, log everything

## Purpose
Cold outreach fails silently: the same template goes out, nobody replies,
and nobody knows whether the problem is deliverability, targeting, the
offer, or the copy. This skill stops that loop. It treats a 0-reply run as a
diagnosis problem first and a writing problem second, and it makes every
send traceable — who got which version, when, and what happened — so the
next decision is evidence, not vibes.

Use it when the user wants to write or rewrite a cold email, a follow-up
sequence, a WhatsApp text, or a call card; when a run has produced zero
replies; when a reply arrives; or when a new outreach run is being set up.
For finding leads, route to `lead-gen` by name — this skill never re-teaches
finding. For job applications, use `job-search`; for social posts, use
`linkedin-craft` or `instagram-craft`.

## Two streams, never blended
Outreach runs in (at least) two different streams with different diseases,
and their numbers must never be mixed:
- **Stream A — cold email to a named person** (e.g. a founder or hiring
  manager at a company). The failure mode is usually deliverability or
  copy: the mail may never arrive, or it arrives and earns no reply.
- **Stream B — local-business outreach** (e.g. small businesses in one
  city). The failure mode is usually the contact route itself: most leads
  publish no business email at all, so email yield is near-zero and the
  reachable channel is a manual text or a call.

Keep a separate log and a separate roll-up per stream. A blended
sent/replied count hides which stream is broken.

## Hard rules (never broken)
- **Diagnose before rewriting.** A 0-reply run gets a diagnosis first —
  see `references/diagnose-zero-replies.md`. Never rewrite on vibes; never
  keep sending the same template past a trigger.
- **Rewrite triggers are hard numbers.** 30 sends / 0 replies = STOP,
  diagnose, propose a rewrite to the owner; no send resumes until the owner
  approves the new template. See `references/diagnose-zero-replies.md` and
  `references/followup-cadence.md`.
- **Verification is a screen, not proof.** A verification score does not
  guarantee delivery. See `references/deliverability.md`.
- **A guess is a guess.** An address built from a name pattern is labelled
  `guess`, never `verified`. Never present a guessed address as confirmed.
- **Draft + approval by default.** Nothing sends without the owner's
  approval for that batch, except a standing auto-flow the owner has
  explicitly left on. Never assume sending is on — a stopped flow stays
  stopped until the owner restarts it in his own words.
- **No bulk cold SMS/WhatsApp.** Unsolicited bulk text carries real legal
  risk (in the US, TCPA penalties run $500–$1,500 per text). WhatsApp texts
  are manual copy-paste by the owner from his own number, one at a time.
  Calls are made by the owner with a prepared card.
- **No fake numbers, no fake claims, no invented social proof.** Every
  claim in a message must be true and checkable. Personalisation must come
  from real research on that lead — a named fact, not flattery.
- **Every send is logged.** Who, which version, when, outcome
  (bounced / delivered / replied). No contact counted twice. See
  `references/logging.md`.
- **A reply is the goal.** When one lands, it jumps the queue: answer fast,
  answer the actual question, move to a call or demo. See
  `references/reply-handling.md`.

## Workflow
1. **Name the stream and the goal.** Stream A or B, what a reply means
   (a call, a demo, an interview), and what "done" looks like for this run.
   If a previous run exists, read its roll-up before writing anything.
2. **Check the trigger state.** Count sends / delivered / bounced / replied
   for this stream since the last rewrite. If a trigger is hit, stop and
   diagnose — do not write the next batch. See
   `references/diagnose-zero-replies.md`.
3. **Verify the route before the copy.** For each contact: is there a
   published email, a verified phone, or neither? Route by what exists —
   email where a published email exists, manual text or call where only a
   phone exists, no channel where neither exists. Never invent an address
   to fill a quota. See `references/deliverability.md` and
   `references/whatsapp-and-calls.md`.
4. **Write one version, one variable.** Short, specific, one ask. One
   named researched fact per message. Log which version each contact got.
   See `references/email-copy.md`.
5. **Send only what was approved.** Drafts go to the owner; sends happen in
   the approved flow and window. Verify each send in Sent mail (or the
   owner's confirmation for manual texts/calls) the same day.
6. **Follow up on schedule, capped.** First follow-up on day 5 after the
   first send; max 2 follow-ups per contact; then close the contact. See
   `references/followup-cadence.md`.
7. **Log, roll up, decide.** Every outcome goes in the same list as the
   daily file. Weekly roll-up per stream: sent / delivered / bounced /
   replied — so the next trigger is visible before the next batch. See
   `references/logging.md`.
8. **Handle replies immediately.** See `references/reply-handling.md`.

## References
| File | What it covers |
|---|---|
| `references/diagnose-zero-replies.md` | The 0-reply diagnosis — four causes, evidence per cause, rewrite triggers |
| `references/email-copy.md` | Cold-email copy — first email, subject lines, personalisation, A/B discipline |
| `references/deliverability.md` | Verify-before-send, bounce handling, sender reputation, verification limits |
| `references/followup-cadence.md` | Follow-up timing, caps, and the stop-and-rewrite triggers |
| `references/whatsapp-and-calls.md` | Manual WhatsApp texts and owner call cards — channel rules, hours, caps |
| `references/logging.md` | The log, dedupe, phone-vs-log check, weekly roll-up |
| `references/reply-handling.md` | What to do the moment a reply lands |

## Provenance
Distilled in our own words from: `first-customer-finder` (MIT);
`scout` v1.3.1 (MIT); `yc-outreach` v1.0 (MIT);
`check-if-email-exists` (MIT, reacherhq/check-if-email-exists);
`google-maps-scraper-kit` (MIT) — merged into `lead-gen` first, and routed
to here by name, not re-taught; plus the working shape of two real outreach
runs (a job-search cold-email run and a local-business email/WhatsApp/call
run): their templates, daily files, contacted log, call cards, and the
failures they recorded — a 30-send / 0-reply rewrite trigger, verification
scores that still bounced, and an email-yield-near-zero local stream. No
source text copied verbatim beyond short terms of art; no project names,
personal data, or credentials carried over. Examples in this skill are
fictionalised.

## Honest limits
- **Verification ≠ delivery.** A check that says "deliverable" can still
  bounce on send. Nothing in this skill guarantees an inbox.
- **0 replies has many causes.** Deliverability, targeting, offer, copy,
  timing, and luck all mix. A diagnosis narrows the cause; it does not
  prove it.
- **No template guarantees replies.** A better template raises the odds;
  it does not promise a reply rate. Never quote one.
- **The agent never sends.** Drafts, logs, diagnoses, and cards are the
  agent's work. Sending — email, text, or call — is the owner's, in the
  owner's approved flow.

## Report format
Stream · trigger state (sends / delivered / bounced / replied since last
rewrite) · diagnosis (if 0 replies) or verdict · drafts (version, who gets
them) · sends approved / sent / verified · follow-ups due · log + roll-up
updated · replies handled · limits.
