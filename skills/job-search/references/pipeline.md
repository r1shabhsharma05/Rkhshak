# Application pipeline — profile, fit, tailor, review, ATS, track

Distilled from `ai-job-search` (MIT, upstream ai-job-search-dev/ai-job-search)
and the one-question-at-a-time elicitation method of `interview-me`.
Own words throughout; the upstream tool's install paths and personal files
are not carried over.

## 1. Profile (the single source of truth)
- One base CV plus a short profile note: real skills, real experience, real
  education dates, real location. Everything downstream is measured against
  this — never against a remembered or improved version.
- Keep a tailored set per posting, filed separately from the base CV, so a
  tailored file is never mistaken for the base one later.

## 2. Clarify before searching
- Ask one question at a time, each with a guess attached ("I guess you want
  backend roles in India — right?"). Listen for what the user actually wants
  versus what they think they should want.
- Restate the goal in the user's own words and get an explicit yes — not
  "whatever you think", not silence. Stop once the next three questions are
  predictable. A confirmed goal is the handoff to discovery; an unconfirmed
  ask never becomes a search.

## 3. Discover (search only)
- Collect postings from boards the user names. Respect robots/ToS for each
  board; a board that blocks scraping is reported, not worked around.
- Discovery never applies, never fills a form, never invents answers.

## 4. Fit scoring (honest, with reasons)
- Score each posting against the real profile. Present the score WITH the
  reasons: every match and every mismatch named (missing skill, years,
  graduation-year cutoff, location/mode).
- A low score is reported as low. The profile is never padded to raise a
  score, and a mismatch the user accepts is recorded as their explicit call,
  not hidden.

## 5. Tailor — drafter-reviewer loop (the core quality trick)
- **Drafter:** tailor the CV and cover letter to that one job description.
  Every bullet traces to real evidence; every keyword comes from that JD.
- **Reviewer (always runs, separate pass):** critique the draft for
  unsupported claims, keyword gaps, and tone. Unsupported means: no measured
  baseline, no production evidence, no source. The reviewer lists each finding
  plainly.
- **Revise:** fix every reviewer finding. A claim that cannot be evidenced is
  cut or replaced with a `[N]` placeholder and a question to the user — never
  swapped for a different invented number.
- Quality over quantity: a few strong-fit applications beat blind volume.
  Never pad the list to hit a number.

## 6. ATS check (before anything goes anywhere)
- Verify the tailored resume parses as clean text (a PDF text-extraction
  check) before it is sent. One page, ATS-clean.
- Keyword match is measured against that JD's keywords. A match target is a
  measurement, not a promise — report the measured figure.

## 7. Outcome tracking (keep the funnel honest)
- Log every application: posting URL, date, tailored files used, submission
  status (confirmed/unconfirmed + evidence), and every outcome (rejection,
  ghost, shortlist, interview, offer). A funnel with no rejections recorded
  is a funnel that is not being tracked.
- Never re-apply to a posting the log shows as already submitted or rejected
  for that posting, unless the user explicitly orders a retry and the log
  records why.
