---
name: job-search
description: "Find roles, score the fit honestly, tailor the CV and cover letter with a drafter-reviewer loop, verify a submission actually landed, prep for interviews, negotiate pay, and write contracts. Use when the user wants to search, apply, prepare, negotiate, or verify any job or freelance engagement. Never invents a skill, experience, number, or company; never applies without the user's pick."
---

# Job Search — find it, fit it, prove it landed

## Purpose
A job hunt fails quietly: a padded resume that collapses in interview, an
application that was never actually submitted, a first offer accepted without
a counter. This skill runs the whole hunt as a checkable pipeline — discovery,
honest fit, tailored application, verified submission, interview prep,
negotiation, contract — with the user's approval at every step that spends
their reputation.

Use it when the user wants to find roles, judge a posting, tailor a resume or
cover letter, check an ATS score, apply, confirm an application went through,
practise interviews, decode an offer, negotiate pay, or write a freelance
contract or proposal. For interview practice specifically, the prep reference
is the entry point; for lead generation and outreach, use lead-gen instead.

## Hard rules (never broken)
- **Nothing invented, ever.** No skill, experience, project, company, metric,
  salary, or graduation year the user did not evidence. Where a number would
  help, write `[N]` and ask for the real value.
- **Quality over quantity.** A few strong-fit applications beat a pile of blind
  ones. Never pad a list to hit a number.
- **The user picks, the user approves.** Present matches with fit ratings; the
  user picks. Nothing is submitted, and no form field is filled with a guessed
  value, without their explicit yes for that application.
- **A submission is unconfirmed until proven.** An "Applied" badge, a closed
  notice, or silence is not a confirmation. See `references/verify-submission.md`.
- **Never live-cheat.** If the user is in a live proctored assessment or
  interview, decline to solve it; offer a debrief afterwards or practice on
  the same pattern once it is over.
- **No timeline or chance promises.** Never quote an odds percentage or a
  hiring timeline the employer did not state.

## Workflow
1. **Clarify the goal first.** If the ask is vague ("find me a job"), run one
   question at a time, each with a stated guess, until the target role, level,
   location/mode, and constraints are explicit — then restate the goal in the
   user's own words and get an explicit yes before searching. Stop asking once
   the next three questions are predictable; do not keep interviewing.
2. **Discover.** Search boards and aggregators for postings only — never apply
   from this step. See `references/discovery-jobspy.md`. Respect each board's
   terms; discovery is read-only.
3. **Score the fit.** Score each posting against the user's real profile
   (skills, experience, graduation year, location). Present the score with the
   reasons, including every mismatch. A low score is reported as low; the
   profile is never padded to raise it.
4. **Tailor.** For a picked posting, tailor the CV and cover letter to that
   job description, then run the reviewer pass: the reviewer critiques the
   draft for unsupported claims, keyword gaps, and tone, and the draft is
   revised. Both passes always run. See `references/pipeline.md`.
5. **ATS check.** Verify the tailored resume parses as clean text before it
   goes anywhere, and that it stays one page and ATS-clean. Keyword match is
   measured against that job description's keywords, never guessed.
6. **Verify the submission.** Check the posting is still open, confirm the
   right file was uploaded, capture the exact confirmation wording, and
   classify follow-up mail. See `references/verify-submission.md`.
7. **Prep.** Mock interviews, resume roasts, company briefs, and prep plans
   from the prep reference. Score like a real interviewer, not a cheerleader.
   See `references/interview-prep.md`.
8. **Negotiate and contract.** Decode the offer, set the three numbers, make
   one consolidated counter. For freelance work, contract before work starts.
   See `references/salary-negotiation.md` and `references/contracts-proposals.md`.

## References
| File | What it covers |
|---|---|
| `references/pipeline.md` | The application pipeline — profile, fit scoring, drafter-reviewer loop, ATS check, outcome tracking |
| `references/discovery-jobspy.md` | Job discovery — board search into a table/CSV, search-only rules, rate and ToS limits |
| `references/interview-prep.md` | Interview prep — mocks, OA sims, system design, HR rounds, resume roasts, company briefs, prep plans, honesty rules |
| `references/verify-submission.md` | Submission verification — open-posting check, upload check, confirmation capture, follow-up mail classification |
| `references/salary-negotiation.md` | Salary negotiation — market data, the three numbers, scripts, counter-offer traps |
| `references/contracts-proposals.md` | Contracts and proposals — clauses, jurisdiction notes, templates, DOCX conversion |

## Provenance
Distilled in our own words from: `ai-job-search` (MIT, ai-job-search-dev/ai-job-search); `jobspy` (MIT, speedyapply/JobSpy); `cracked` v1.3.0 (MIT, 19-skill interview-prep pack); `interview-me` (one-question-at-a-time elicitation method, used here only for step 1); `salary-negotiator`; `contract-and-proposal-writer` (MIT); `verify_job_submission` (MIT). No source text copied verbatim beyond short terms of art; no project names, personal data, or credentials carried over.

## Report format
Fit (score + named matches/mismatches) · tailored files (what changed, reviewer findings fixed) · ATS result · submission status (confirmed / unconfirmed + evidence quoted) · prep scorecard (if any) · next step (one line, owned by the user where approval is needed).
