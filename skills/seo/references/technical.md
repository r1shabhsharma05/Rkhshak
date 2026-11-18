# Technical SEO

## 1. Crawlability
- robots.txt reachable, deliberate, and not blocking important resources. Sitemaps declared and reachable.
- Status codes: every important URL returns 200; redirects point at the final URL; no redirect chains.
- Crawl budget: for large sites, watch Search Console crawl stats; noindex low-value filtered views rather than letting them eat the budget.

## AI crawler management
Different bots do different jobs — check the right bot for the claim being made:
| Crawler | Purpose |
|---|---|
| GPTBot | Model training only (NOT ChatGPT Search) |
| OAI-SearchBot | ChatGPT Search citability |
| ChatGPT-User | User-triggered browsing (may not obey robots.txt) |
| ClaudeBot | Model training only |
| Claude-SearchBot | Claude search-result citability |
| PerplexityBot | Perplexity search index (not training) |
| Bytespider | Model training |
| Google-Extended | Gemini training and grounding (no effect on Search inclusion or ranking) |
| Applebot-Extended | Apple Intelligence training opt-out (not Siri/Spotlight/Safari) |
| CCBot | Common Crawl open dataset |

Blocking a training bot does not remove a site from search; blocking a search bot does not stop training. Say which one the user is actually blocking.

## 2. Indexability
- No accidental noindex (meta or header). Canonicals self-referencing and consistent.
- Canonical conflicts: if raw HTML and JavaScript inject different canonicals, the search engine may use either — keep them identical.
- Noindex in raw HTML that JavaScript later removes may still be honoured — serve the correct directive server-side.
- Pages returning non-200 are not rendered for JavaScript content; anything JS-injected on an error page is invisible.

## 3. Security (read-only flags — fixes belong to security-audit)
- HTTPS everywhere, no mixed content, no HTTP links to important pages.
- Security headers present; exposed server/stack versions flagged (never probed aggressively).
- Flag pages that defeat the Back button via history manipulation — a spam-policy violation, not a UX quirk.

## 4. URL structure
Clean, readable, keyword-bearing, lowercase, hyphens not underscores, no parameters or session IDs, no double slashes, no non-ASCII. Short beats clever.

## 5. Mobile optimisation and page experience
- Mobile/desktop content parity is the highest-value mobile check: equivalent primary content, matching robots meta, matching titles/descriptions, equivalent structured data, crawlable resources.
- No intrusive interstitials, no standalone consent-redirect pages, no persistent blocking dialogs, no excessive ad density.
- Key content visible on load — not hidden behind tabs or accordions that require interaction; do not hijack scroll on load; preserve URL hash fragments.

## 6. Core Web Vitals (field data, p75)
| Metric | Good |
|---|---|
| LCP (Largest Contentful Paint) | ≤ 2.5s |
| INP (Interaction to Next Paint) | ≤ 200ms |
| CLS (Cumulative Layout Shift) | ≤ 0.1 |

Lab numbers are a diagnostic, not the verdict — the verdict is field data (CrUX / PageSpeed Insights). If lab and field disagree, trust field and say so.

## 7. Structured data
Present, valid, and matching the visible page. Mismatched or invisible markup is worse than none. See `schema-and-sitemap.md` for which types still earn rich results.

## 8. JavaScript rendering
| Strategy | Use for |
|---|---|
| SSR | Public SEO content, dynamic pages |
| SSG | Static content, blogs, docs |
| CSR | Authenticated / behind-login content only |

Structured data injected by JavaScript may face delayed processing — for time-sensitive markup (notably e-commerce Product), render it server-side.

## 9. IndexNow
Submit changed URLs to IndexNow where the engine supports it, as a complement to sitemaps — never as a replacement for fixing crawlability.
