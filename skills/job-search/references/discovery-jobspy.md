# Job discovery — board search into a table, search only

Distilled from `jobspy` (MIT, speedyapply/JobSpy, Python job-posting
aggregator). Own words; install paths and local configuration are not
carried over — follow the tool's own README on the machine where it runs.

## What it does
- Aggregates postings from major boards (LinkedIn, Indeed, Glassdoor,
  ZipRecruiter, Naukri, Bayt, BDJobs, HelloWork) into a table/CSV with the
  fields that matter for shortlisting: title, company, location, date posted,
  job URL, and description where available.
- Search is the whole job. This reference never applies, never fills a form,
  never invents answers.

## Workflow
1. **Take the search from step 1 of the pipeline** — role, level, location,
   remote/onsite, and any must-have/must-not filters. A vague search returns
   a vague list; pin the filters first.
2. **Run one board batch at a time.** Small validation first (a handful of
   results, eyeballed) before any wide run.
3. **Present as a shortlist, not a dump.** Title, company, location, posted
   date, URL, and a one-line fit note per posting. Duplicates across boards
   are merged on the posting URL, not the title.
4. **Hand the shortlist to fit scoring** (`pipeline.md` step 4). The user
   picks; discovery does not pick for them.

## Rules
- **Search only.** No application, no form fill, no account creation from
  this step. Applying is a separate, user-approved step.
- **Respect the board.** Obey rate limits and terms of use. A board that
  throttles, CAPTCHAs, or blocks is reported and stopped — do not hammer
  retries or rotate proxies to evade a block.
- **Stale is stale.** A posting found by an aggregator is unverified until
  the official posting confirms it is open (see `verify-submission.md`).
  Never present an aggregator listing as a live opening.
- **No invented postings.** Every row traces to a fetched posting URL. A
  posting with no reachable URL is not listed.
