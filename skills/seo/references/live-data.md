# Live data (Google APIs and DataForSEO)

## Rule zero: cost before spend
Show the cost estimate and get explicit approval before any paid call. State which tier a result came from, so the user knows what it cost and what it can prove. Never present a third-party estimate as Google's own data.

## Google API tiers
| Tier | Credential | Available |
|---|---|---|
| 0 (API key) | API key | PageSpeed, CrUX, CrUX history, YouTube search, NLP |
| 1 (OAuth / service account) | Tier 0 + OAuth token or service account | Tier 0 + Search Console, URL Inspection, Sitemaps, Indexing API |
| 2 (Full) | Tier 1 + GA4 property id | Tier 1 + GA4 organic traffic, top landing pages |
| 3 (Ads) | Tier 2 + Ads developer token + customer id | Tier 2 + Keyword Planner ideas and volume |

## What each source proves
- **PageSpeed Insights v5**: lab Lighthouse + CrUX field data for a URL. Lab is diagnostic; field is the verdict.
- **CrUX**: real-user Core Web Vitals, p75, with 25-week history for trends. If a URL has no CrUX data, say so — do not substitute lab numbers silently.
- **Search Console**: clicks, impressions, CTR, position per query/page; index status and canonical per URL via URL Inspection; sitemap status. This is the site's own data — the most trustworthy source in this skill.
- **Indexing API**: submit URLs for crawling (job postings and livestreams are the supported types for most sites — do not present it as a general "index faster" button).
- **GA4**: organic traffic and top organic landing pages. Organic only — never mix in paid or direct.
- **Keyword Planner**: keyword ideas and volume ranges. Volume is a range, not a count — report it as one.
- **NLP API**: entity extraction, sentiment, classification — useful for E-E-A-T entity checks, not for ranking claims.

## DataForSEO (paid)
SERP analysis, keyword research (volume, difficulty, intent, trends), backlink profiles, on-page analysis, competitor and content analysis, business listings, AI visibility (LLM mention tracking), domain analytics, YouTube deep analysis. Every call consumes credits: estimate first, confirm, then run. Report credits consumed in the output.

## Free fallbacks (when no paid access exists)
Common Crawl for backlink graphs, PageSpeed/CrUX with a free API key, Search Console (free, needs ownership), manual SERP reading. A free-tier audit that says what it could not check is worth more than a paid-tier audit that pretends.

## Rate limits and quotas
Every API here has quotas. Check them before a batch (notably URL Inspection batch and Indexing batch, capped per day). On a 429, back off and report partial results — never retry in a tight loop.
