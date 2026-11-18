# Audit and scoring

## Full-site audit process
1. Render the homepage: capture raw HTML, rendered HTML, extracted text, whether the page is a single-page app, and accessibility basics.
2. Detect the business type from homepage signals — never assume it:
   - SaaS: pricing page, /features, /integrations, /docs, "free trial", "sign up".
   - Local service: phone number, address, service area, "serving [city]", Maps embed — suggest the local workflow for a deeper pass.
   - E-commerce: /products, /collections, /cart, "add to cart", product schema.
   - Publisher: /blog, /articles, /topics, article schema, author pages, publication dates.
   - Agency: /case-studies, /work, /industries, "our work", client logos.
3. Crawl: follow internal links, cap 500 pages, respect robots.txt.
4. Run the category checks (technical, content, on-page, schema, performance, AI readiness, images) — sequentially if no parallel help is available.
5. Score, then write artifacts under `{domain}-audit/` and report.

## Score weights (0–100)
| Category | Weight |
|---|---|
| Technical SEO | 22% |
| Content Quality | 23% |
| On-Page SEO | 20% |
| Schema / Structured Data | 10% |
| Performance (Core Web Vitals) | 10% |
| AI Search Readiness | 10% |
| Images | 5% |

## Priority definitions
- **Critical**: blocks indexing or risks a penalty. Fix immediately.
- **High**: significantly impacts rankings. Fix within 1 week.
- **Medium**: optimisation opportunity. Fix within 1 month.
- **Low**: nice to have. Backlog.

## Single-page checks (deterministic, from the page itself)
| Area | Finding ids |
|---|---|
| Title, description | `missing-title`, `title-too-long`, `title-too-short`, `missing-meta-description`, `meta-description-too-long`, `duplicate-meta-tags` |
| Headings | `missing-h1`, `multiple-h1`, `heading-level-skip` (main content only) |
| Canonical, robots | `missing-canonical`, `canonical-points-elsewhere`, `og-url-differs-from-canonical`, `noindex`, `noindex-header`, `nofollow`, `meta-refresh-redirect`, `hreflang-missing-self` |
| Document basics | `missing-doctype`, `missing-charset`, `charset-mismatch`, `missing-lang`, `missing-viewport`, `uses-frames`, `deprecated-html-tags`, `placeholder-text` |
| Images | `images-missing-alt`, `images-missing-dimensions`, `first-image-lazy-loaded` |
| Links | `links-without-text`, `generic-anchor-text`, `links-to-http`, `mixed-content` |
| URL | `url-too-long`, `url-has-parameters`, `url-uppercase`, `url-underscores`, `url-non-ascii`, `url-double-slash` |
| Size | `html-over-2mb`, `deep-dom`, `wide-dom-node` |
| Social, schema | `missing-open-graph`, `missing-og-image`, `invalid-jsonld` |
| Content | `title-not-reflected-in-content`, `description-not-reflected-in-content`, `thin-content` |

Title target 50–60 characters; meta description 150–160. One H1 per page. Core Web Vitals are reference-only from HTML alone — they need field data (see `live-data.md`).

## Report structure
Executive summary → score table → Technical → Content → On-Page → Schema → Performance → Images → AI Search Readiness → prioritised action plan. Each finding names the URL, the observed value, and the fix.

## Error handling
| Scenario | Action |
|---|---|
| URL unreachable (DNS, connection refused) | Report the error clearly. Do not guess site content. Ask the user to verify the URL. |
| robots.txt blocks crawling | Report which paths are blocked. Analyse only accessible pages and note the limitation. |
| Page requires authentication (401/403) | Report it is behind authentication. Ask for the rendered HTML or a public URL. |
| Rate limiting (429) | Back off, reduce concurrency, report partial results and what could not be checked. |

## Synthesis rule
Walk PERCEIVE → ANALYZE → VALIDATE → ACT before bucketing findings into Critical / High / Medium / Low. A finding without observed evidence is a hypothesis — label it one, never a score deduction.
