# Schema and sitemaps

## Schema: detect, validate, generate
1. **Detect**: JSON-LD, Microdata, RDFa on the page. Record every type found.
2. **Validate**: syntax (missing brackets, trailing commas, unquoted keys), required fields per type, and whether the markup matches what the page visibly shows.
3. **Generate**: only for types that are active (below). Never generate markup for content the page does not have.

## Schema type status (checked October 2026 — re-verify before recommending, statuses change)
**Recommend freely**: Organization, LocalBusiness, Article / BlogPosting, Product, BreadcrumbList, VideoObject and other video types, Dataset (for Dataset Search only — no Google Search rich-result surface, do not present it as one).
**No rich results, keep if useful**: FAQPage — Google retired FAQ rich results for all sites on 7 May 2026. Flag existing FAQPage at Info, not Critical. QAPage only for genuine user Q&A.
**Never recommend**: HowTo (rich results removed September 2023), SpecialAnnouncement (deprecated 31 July 2025), CourseInfo / EstimatedSalary / LearningVideo (retired June 2025), ClaimReview (no Search rich result since June 2025 — fact-checking publishers may keep it for Fact Check Explorer, never recommend it for SERP features), VehicleListing (retired June 2025), Practice Problem (deprecation notice 5 November 2025; tooling support removed from January 2026).
**Still supported despite earlier phase-out notices**: Book Actions (the June 2025 phase-out banner was removed on 5 November 2025 because a Search feature still uses the markup).

Common templates: Organization (name, logo, URL, social profiles), LocalBusiness (name, address, phone, hours, geo), Article/BlogPosting (headline, author, dates, image). Keep markup and visible content in agreement — mismatched markup is worse than none.

## Sitemaps: analyse
| Check | Rule |
|---|---|
| Per-file limit | ≤ 50,000 URLs AND ≤ 50MB uncompressed — split with a sitemap index above either |
| Index structure | An index lists sitemaps, never another index (nested index is not followed) |
| `<lastmod>` | Present, valid W3C datetime, actual modification dates — a file where every URL shares one lastmod is a signal the dates are fake |
| Host | URLs must live on the same host as their sitemap (cross-host URLs are ignored) |
| Tokens | No session IDs or tokens in listed URLs (redact them in reports) |
| robots.txt | Sitemap referenced there |
| Contents | Only 200, indexable, canonical URLs — no noindexed, redirected, or broken URLs |
| Priority / changefreq | Can be removed; Google ignores them |
| Extension sitemaps | Image (only the valid image fields), Video (requires thumbnail_loc), News (max 1,000 entries per file) |

## Sitemaps: generate
Process: discover URLs (crawl or URL list) → filter to canonical, indexable 200s → split at the limits above → write the index → declare it in robots.txt → submit in Search Console. Report counts per file and what was excluded, with reasons.
