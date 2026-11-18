---
name: lead-gen
description: "Find evidence-backed first customers and leads from public signals, score and shortlist them, draft outreach that is never sent by the agent, and verify contact details honestly. Use when the user wants prospects, a first-customer shortlist, local-business leads, founder outreach, freelance clients, or a checked email address. Scraped data is a lead list, not verified truth."
---

# Lead Gen — evidence first, drafts only, verify before contact

## Purpose
A lead list is only as good as its evidence. A name with no cited pain is a
guess, a guessed email is not a contact, and a sent message the user never
approved is a reputation spent. This skill finds prospects from public demand
signals, qualifies them against evidence, drafts outreach for the user to
send, and verifies contact details within honest limits.

Use it when the user wants first customers, beta users, or design partners;
local-business leads; social-platform leads; founder outreach lists; freelance
clients and pipeline; or an email address checked before outreach. For job
applications, use job-search; for publishing content, use linkedin-craft.

## Hard rules (never broken)
- **Evidence-backed only.** A prospect without a cited pain, need, or timing
  signal is speculative-fit only and never appears in the primary shortlist.
  Never fill a quota with weak matches.
- **Drafts only — nothing is sent by the agent.** No messages, form submits,
  connects, follows, comments, or CRM records unless the user separately
  requests and authorises that specific action.
- **A guess is a guess.** An email built from a name pattern is labelled
  `guess`, never `verified`. Verify first, then contact.
- **Scraped data is untrusted.** A bio, a listing, or a guessed address is a
  lead, not proof it is current or correct. Verify before calling or emailing.
- **Call-first where a phone route exists.** Never lead with bulk cold
  SMS/WhatsApp. Bulk blasts are not authorised by this skill.
- **Public data only.** No login walls, paywalls, access controls, rate-limit
  or robots bypasses, data brokers, leaked datasets, private groups, or
  personal-email/phone enrichment. No inferring protected traits; no targeting
  on health, financial hardship, political belief, sexuality, or religion.
- **Never claim interest.** Never say a prospect is interested, has consented,
  or will buy. The label is always "potential customer based on public signals".

## Workflow
1. **Understand the product.** One paragraph: what it does, who it is for,
   what pain it removes, what it cannot do. A prospect that needs a missing
   capability is excluded, not scored.
2. **Build a public-signal search plan.** Multiple query angles and source
   types (public posts, issues, forums, reviews, company pages). Search
   engines are discovery aids, not evidence — open the original pages.
3. **Research safely.** Public, intentionally shared professional/business
   information only. Record publication date separately from the date checked;
   attribute each signal to its actual author/company.
4. **Qualify and deduplicate.** Score each prospect on pain strength, product
   fit, timing, public reachability, and evidence quality. A high number never
   overrides contradictory evidence. Put counter-evidence in the caution or
   exclude the candidate. See `references/first-customer.md`.
5. **Verify the contact route.** A concrete official/public route with its URL
   and why it fits — or say no route was found and give a manual next step,
   never a guessed address. Email checks: `references/email-verify.md`.
6. **Draft outreach, never send.** One short opener in the buyer's problem
   language, a specific low-friction CTA, no claimed asset/integration/result
   unless verified. See `references/yc-outreach.md` for founder lists and
   `references/scout.md` for social-platform leads.
7. **Report and refine.** Verdict, ICP, top prospect, shortlist, repeated
   patterns, a 7-day manual low-volume plan, and limits. Invite short feedback
   by prospect ID and refine — do not delay the first report waiting for it.

## References
| File | What it covers |
|---|---|
| `references/first-customer.md` | First-customer finding — public-signal research, qualification framework, report shape |
| `references/scout.md` | Social-platform leads — 8 platforms, enrichment, 0–100 scoring, CSV export |
| `references/maps-scraper.md` | Local-business leads from Maps — queries, depth, filters, rate limits, scraped-data rules |
| `references/yc-outreach.md` | Founder outreach lists — batch search, guess labels, verify-first, draft-only |
| `references/freelance-practice.md` | Freelance practice — positioning, pricing, pipeline, contracts, scope creep |
| `references/email-verify.md` | Email checks — verdicts, SMTP limits stated honestly, deliverability routing |
| `references/web-research-ops.md` | Web research operations — routing a research question, site-to-API, read-only browser checks |

## Provenance
Distilled in our own words from: `first-customer-finder` (MIT); `scout` v1.3.1 (MIT, kiryano/Scout); `google-maps-scraper` (MIT) and `google-maps-scraper-kit` (MIT, merged — same method, two harnesses); `yc-outreach` v1.0 (MIT, adityajha2005/yc-founder-outreach); `freelance-guide`; `check-if-email-exists` (MIT, reacherhq/check-if-email-exists); `render_free_email_delivery` (SMTP-blocked → provider HTTP API); `agent-reach` (MIT, Panniantong/Agent-Reach); `api-anything`; `agent-browser`; `browser-use` (MIT). No source text copied verbatim beyond short terms of art; no project names, personal data, or credentials carried over.

## Report format
Verdict (reachable early-customer signals: yes/no) · ICP (buyer, job, trigger, disqualifiers) · top prospect (strongest evidence, why now) · shortlist (ID, source/date, score, why now, target role, verified contact route or missing route, next step, CTA, opener, caution) · patterns · 7-day manual plan · limits (missing evidence, what real conversations must confirm).
