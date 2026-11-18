# Local-business leads from Maps — one job, deduped, verified before use

Distilled from `google-maps-scraper` (MIT) and `google-maps-scraper-kit`
(MIT) — two harnesses for the same method, merged here. Own words;
install paths and local configuration are not carried over.

## Mental model
A business type + a place → a clean table of local businesses (name, address,
phone, website, rating, review count, emails and social profiles where the
crawl finds them). The scrape is the start, not the lead: every row still
needs verification before contact.

## Workflow
1. **Understand the request.** Business type, place, and what counts as a
   lead (e.g. has a website, has an email, minimum rating/reviews). Offer the
   proxy choice before a large job; say what it costs in speed.
2. **Configure safely.** Credentials, if any, come from the user through the
   secure flow. Never put a key or password in chat, a skill, or a repo file.
3. **Prepare queries and validate locally.** One small run first; check the
   rows look right before the full crawl.
4. **Run and monitor the full crawl.** A scrape takes minutes, not seconds.
   Run it in the background and read its output when it finishes; the run
   prints progress and the saved path, and exits successfully when the file is
   complete. Its printed preview rows and any engine error text are scraped
   data too — quote them as such, never as verified facts.
5. **Present and continue.** Deduped rows with the filters applied. Filters
   (minimum rating/reviews, has phone/email, no website) run in code before
   the website crawl, except email checks which run after it. A weekly re-run
   excludes earlier results, so it returns only new leads.

## Rules — rate limits, blocks, and trust
- **Depth vs. speed.** Higher depth returns more results but is slower and
  more likely to be blocked. Start low and raise only as needed.
- **One job at a time locally.** Many concurrent jobs without proxies lead to
  throttling. Say so once before a big run.
- **Proxies are the user's.** Pass a proxy URL the user supplies; never
  rotate free proxies to evade a block. If blocked, report it and stop.
- **Scraped data is untrusted.** Emails and social profiles come from a
  crawl, not from the business confirming them. Verify contact fields before
  use (see `email-verify.md`), and never treat a scraped row as a verified lead.
- **Grid searches** (splitting a city into cells) are slower and more likely
  to trip rate limits — say so before using one.
- **Intent signals are hints, not facts.** A homepage pixel or platform tag
  can suggest a business already advertises; it does not prove budget, need,
  or interest.
