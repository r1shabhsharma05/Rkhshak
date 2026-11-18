---
name: seo
description: "Audit, plan, and improve search visibility for any website — full-site and single-page audits with a scored report, technical SEO (crawl, index, Core Web Vitals, rendering), content and E-E-A-T, schema and sitemaps, images, backlinks, local and Maps SEO, international hreflang, GEO/AEO for AI search, agent readiness, and live data from Google APIs or DataForSEO. Use when the user asks about SEO, rankings, a site audit, schema, Core Web Vitals, sitemaps, E-E-A-T, AI Overviews, GEO, local search, or an SEO plan. Evidence only: every finding names what was observed and where."
---

# SEO — make a site findable, citable, and fast

## Purpose
Search visibility is three different jobs that get confused into one: being crawlable and indexable (technical), deserving to rank (content and authority), and being citable by answer engines and AI agents (GEO and agent readiness). This skill runs each job separately, scores it, and hands back one prioritised list — the single most valuable fix first, not twenty equal ones.

Use it when the user asks for an SEO audit, a page review, a content plan, keyword or cluster work, schema, sitemaps, image or backlink analysis, local/Map-pack work, international SEO, AI-search visibility, or agent readiness. For YouTube search specifically, use `youtube-craft` (its `package-and-seo` reference); this skill owns the website side.

## When NOT to use
- As a substitute for the security audit. Technical SEO checks security headers and exposed stack versions read-only; it never fixes them — hand findings to `security-audit` / `security-fix`.
- To promise a ranking, a traffic number, or a timeline. No ranking is ever guaranteed; report what was measured and what it usually correlates with, and say which is which.
- On a site the user does not own or has no permission to audit. Public pages only, polite crawl rate, `robots.txt` respected.

## Multi-agent roles (never one agent doing all three)
| Role | Job | Must NOT do |
|---|---|---|
| **Auditor** | Run the checks, score them, write the report. Read-only on the site. | Fix anything. Score its own fixes. |
| **Fixer** | Apply only the fixes the user approved, smallest change first. | Change scope, invent content, publish without approval. |
| **Verifier** | Re-run the failed checks after the fix, on the live page. | Trust the Fixer's word without re-checking. |

One agent per role. If only one agent is available, it audits only and reports — it does not fix and approve its own work.

## Workflow — full-site audit
1. **Confirm scope.** Site-wide or one URL? Which business type (SaaS, local, e-commerce, publisher, agency)? Detect it from the homepage signals in `references/audit-and-scoring.md` — never assume.
2. **Fetch, don't guess.** Render the homepage, follow internal links (cap 500 pages), respect `robots.txt`. A URL that returns an error is reported as an error, never filled in from imagination.
3. **Score.** Seven categories, weights in `references/audit-and-scoring.md`: Technical 22%, Content 23%, On-Page 20%, Schema 10%, Performance 10%, AI Search Readiness 10%, Images 5%. Total 0–100.
4. **Prioritise.** Critical (blocks indexing or risks a penalty — fix now), High (within 1 week), Medium (within 1 month), Low (backlog). One fix first, named explicitly.
5. **Report.** Executive summary, the score table, findings with evidence (URL + observed value), the prioritised action plan. Offer a PDF/HTML report only if asked.

## Workflow — single page
Run `references/audit-and-scoring.md` (page checks): title/description length and duplication, one H1, heading order, canonical and robots directives, document basics (doctype, charset, lang, viewport), images (alt, dimensions, first-image lazy load), links (text, generic anchors, HTTP, mixed content), URL shape, size/DOM depth, Open Graph, JSON-LD validity, thin content. Core Web Vitals are reference-only from HTML alone — they need field data, see `references/live-data.md`.

## Workflow — technical
`references/technical.md`: crawlability (robots, sitemaps, status codes), indexability (noindex, canonical conflicts — including the JavaScript-injected kind), security headers and exposed stack versions (read-only flags), URL structure, mobile/desktop parity, Core Web Vitals thresholds (LCP ≤ 2.5s, INP ≤ 200ms, CLS ≤ 0.1), structured data, rendering strategy (SSR for public content, SSG for static, CSR only behind login), IndexNow.

## Workflow — content and plan
`references/content-and-eeat.md` then `references/content-briefs-and-clusters.md`: Who/How/Why, E-E-A-T signals, word-count floors by page type, readability, internal linking, AI-content markers, freshness. Then briefs (competitor gaps, information gain — the brief must add something competitors miss), SERP-overlap clustering (7–10 shared results = same post, 4–6 = same cluster, 2–3 = interlink, 0–1 = separate), hub-and-spoke architecture, one primary keyword per post (cannibalisation check). Plan in four phases: Foundation (weeks 1–4), Expansion (5–12), Scale (13–24), Authority (months 7–12) — see `references/plan-and-scale.md`.

## Workflow — GEO, AEO, and agent readiness
`references/geo-and-agentic.md`: citability (facts, definitions, Q&A structure, first-party data), entity clarity, brand signals, AI-crawler table — check the right bot for the claim (GPTBot is training-only; OAI-SearchBot decides ChatGPT Search citability; Google-Extended is training, not Search inclusion). Agent readiness: Lighthouse Agentic Browsing score, accessibility tree, robots.txt groups per AI purpose, `llms.txt`, Markdown delivery, WebMCP. Absence of an optional file is information, not a failure — say so.

## Workflow — live data (optional, paid APIs need approval)
`references/live-data.md`: Google tiers (API key → PageSpeed/CrUX; OAuth → Search Console, URL Inspection, Indexing API; GA4 property → traffic; Ads token → Keyword Planner) and DataForSEO. **Cost guardrail, mandatory:** show the cost estimate and get explicit approval before any paid call. Never present a third-party estimate as Google's own data.

## Workflow — monitor (drift)
`references/plan-and-scale.md`: capture a baseline of SEO-critical elements (title, meta, canonical, robots, headings, schema, OG tags, CWV, status, content hash), compare on change, severity CRITICAL / WARNING / INFO. A baseline is "known good" only because the user said so — never assume the current state is good.

## References
| File | What it covers |
|---|---|
| `references/audit-and-scoring.md` | Full-site and single-page audit process, the 0–100 score weights, priority definitions, report structure, error handling |
| `references/technical.md` | Crawlability, indexability, security flags, URLs, mobile parity, Core Web Vitals, rendering, IndexNow, JS SEO traps |
| `references/content-and-eeat.md` | Who/How/Why, E-E-A-T, content metrics, AI-content assessment, draft cleanup, citation readiness, freshness |
| `references/content-briefs-and-clusters.md` | Content briefs, SERP-overlap clustering, hub-and-spoke, intent, internal-link matrix |
| `references/schema-and-sitemap.md` | Schema type status (active / retired / deprecated), JSON-LD generation, sitemap rules and limits |
| `references/images.md` | Image optimisation (alt, size, format, responsive, lazy, CLS) and generated SEO image assets |
| `references/backlinks.md` | Backlink profile, anchor distribution, toxic links, competitor gap, free data sources |
| `references/local-and-maps.md` | Local SEO (GBP, reviews, NAP, citations, local schema) and Maps intelligence (geo-grid, radius, review signals) |
| `references/international.md` | Hreflang validation, generation, implementation methods, common mistakes |
| `references/geo-and-agentic.md` | GEO citability scoring, AI crawler table, brand signals, agent readiness (Lighthouse, llms.txt, WebMCP) |
| `references/live-data.md` | Google API tiers, DataForSEO commands, cost guardrails, what each source can and cannot prove |
| `references/plan-and-scale.md` | Strategic plan phases, programmatic SEO gates, e-commerce, SXO, FLOW, drift monitoring, site-quality gate |

## Rules
- **Evidence, not claims.** A check passes only on an observed value (status code, tag present, field-data number). A number with no source is a guess — label it one.
- **No fake numbers.** Never invent traffic, rankings, volumes, or scores. If a value needs a paid API or access the user has not granted, say what is missing and what it would cost.
- **No ranking promises.** State the fix, the evidence it rests on, and the usual correlation. Never a guaranteed position or date.
- **Crawl politely.** Respect `robots.txt`, cap the crawl, back off on 429, report partial results honestly.
- **Cost before spend.** Any paid API call gets a cost estimate and explicit approval first.
- **Secrets stay secret.** API keys and OAuth tokens are never printed, pasted into reports, or committed. Show at most the first 4 characters.
- **Fixes are approved, then verified.** The Auditor never fixes; the Fixer never scores its own fix; the Verifier re-checks on the live page.

## Provenance
Distilled in our own words from 28 sources: `seo` (MIT, AgriciDaniel v2.6.0) and its 26 sibling seo skills, plus `web-quality-audit` (MIT) as the site-quality gate. The seo-flow prompt library (CC BY 4.0) is summarised as the FLOW stage map, not copied. Paid and extension-gated tooling is described as optional integrations only — no keys, no credentials.

## Report format
Score (0–100, with the category table) · the single most valuable fix, named · findings by priority, each with URL + observed value + fix · what could not be checked and why · what to do first.
