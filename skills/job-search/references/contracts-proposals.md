# Contracts and proposals — clauses, jurisdiction, templates

Distilled from `contract-and-proposal-writer` (MIT). Own words; clause
summaries are general information, not legal advice — the user should have a
lawyer review anything binding.

## When to use
Freelance contracts, project proposals, statements of work (SOWs), NDAs, and
MSAs. Drafting only — the user signs, never the agent.

## Workflow
1. **Gather requirements.** Parties, scope/deliverables, timeline, payment
   terms, jurisdiction, and who owns what. Ask for what is missing; never
   fill a legal fact by guessing.
2. **Select the template.** Fixed-price build, hourly/retainer, SOW, NDA, or
   MSA — match the engagement, not the nearest file.
3. **Generate and fill.** Structured Markdown output. Every filled value
   traces to something the user stated; every unknown is a bracketed
   placeholder, never an invented value.
4. **Convert to DOCX** (e.g. via pandoc) when the counterparty needs a Word
   file. Keep the Markdown as the source of truth.

## Key clauses reference (check every draft for each one)
- **Services / scope.** Exactly what is delivered, and what is out of scope.
  Vague scope is where disputes are born.
- **Payment.** Amount, schedule, deposit (typically 30–50% upfront), late fee,
  net terms (net-15 / net-30). Final payment triggers IP transfer, not the
  other way round.
- **Intellectual property.** Who owns the work, when ownership transfers
  (on final payment), and what licence the client gets before then.
- **Confidentiality.** What is confidential, for how long, and the carve-outs.
- **Warranties.** What is promised (and, honestly, what is not).
- **Liability.** Caps, exclusions, and what happens when things go wrong.
- **Termination / kill fee.** How either side ends it, notice period, and what
  is owed for work done plus a kill fee. A draft with no termination clause
  is not ready to sign.
- **Dispute resolution.** Governing law and venue — this is where jurisdiction
  bites.
- **General.** Entire agreement, amendments in writing, severability.

## Jurisdiction notes (never apply one region's defaults silently)
- **US (Delaware).** Common for US tech contracts; note choice-of-law and
  arbitration clauses explicitly.
- **EU (GDPR).** Data-processing terms matter the moment personal data is
  handled; name the data, the purpose, and the retention.
- **UK (post-Brexit).** UK law and GDPR-UK are separate from EU GDPR —
  do not copy EU clauses verbatim.
- **DACH (Germany / Austria / Switzerland).** German-law contracts have
  their own form and termination norms; flag where local law overrides a
  template's assumptions and get local review.

## Standing rule
**Contract before work.** Scope, deliverables, timeline, payment terms,
revision rounds, kill fee, IP transfer on final payment. Never start without
a signature and (ideally) a deposit. A one-page agreement prevents most
disputes; "they seemed trustworthy" precedes most freelancer horror stories.
