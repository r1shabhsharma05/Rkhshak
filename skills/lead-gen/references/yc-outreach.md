# Founder outreach lists — batch search, guess labels, verify first

Distilled from `yc-outreach` v1.0 (MIT, adityajha2005/yc-founder-outreach).
Own words throughout.

## What it does
Pick a startup batch (e.g. a Y Combinator batch), get every company's
founders and their likely email addresses, and draft one personalised cold
email at a time. Free by default — no account, no API key; optional verified
emails with the user's own enrichment token.

## Email reliability (labels, best source first)
- `verified` — checked by an enrichment service.
- `unverified` — looked up, unconfirmed.
- `on site` — published on the company homepage or contact page.
- `guess` — built from a name pattern (`first@domain`, `first.last@`,
  `flast@`, `firstlast@`). In the upstream check against enrichment-verified
  founder emails, the first guess was right most of the time and the right
  address was in the guess list most of the time — but a `guess` is NOT a
  verified address. Treat it as a lead, not a confirmed contact.
- **Verify-first, always:** pre-filter every guessed address (see
  `email-verify.md`), then a deliverability check, before any send.

## Workflow
1. Pick the batch and pull the company + founder list. Bulk export to JSON/CSV
   is for the list, not for sending.
2. For each founder, one at a time: confirm the company, the founder's role,
   and the best email label. Never invent a named decision-maker.
3. Draft one short personalised email from a single template: their problem
   language, one concrete reason to talk, one low-friction CTA.
4. Hand the draft to the user. Sending stays in the user's approved flows.
   Nothing auto-sends.

## Guardrails
- **Drafts only.** This reference writes email text; it never sends anything.
- **One person at a time, keep it short, take "no" for an answer.**
- **Call-first where a phone route exists.** Never lead with bulk cold
  SMS/WhatsApp — the legal risk of unsolicited bulk text is real money per
  message. Bulk email blasts are not authorised by this skill.
- **Keys come from the user** through the secure flow, as environment
  variables only. Never paste a token in chat, never commit a `.env` file.
- Founders are a different audience from local businesses: the pitch is a
  fit conversation, not a volume play.
