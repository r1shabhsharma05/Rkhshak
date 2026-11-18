# Plan and scale

## Strategic plan (four phases)
1. **Discovery**: business type, current state, competitors, keyword landscape, technical baseline.
2. **Competitive analysis**: who ranks, for what, with what content and links — and what they miss.
3. **Architecture design**: site structure, URL patterns, hub-and-spoke map.
4. **Content strategy**: clusters, briefs, E-E-A-T requirements.
5. **Technical foundation**: crawl, index, speed, schema — fixed before scale, not during it.
6. **Roadmap**:
   - Phase 1 Foundation (weeks 1–4): technical fixes, analytics, core pages.
   - Phase 2 Expansion (weeks 5–12): first clusters, briefs, internal links.
   - Phase 3 Scale (weeks 13–24): more clusters, programmatic where justified, local/international where relevant.
   - Phase 4 Authority (months 7–12): links, original data, brand signals.
- KPI targets are set per phase as baselines with 3/6/12-month checkpoints (organic traffic, keyword rankings, indexed pages, Core Web Vitals). Targets are the user's numbers, never invented — if no baseline exists, the first checkpoint is "measure", not a number.

## Programmatic SEO (pages at scale)
- **Data first**: assess the source (CSV/JSON row count and uniqueness, API freshness and rate limits, database completeness) before any template.
- **Templates**: variable injection points (title, H1, body sections, meta, schema), static vs dynamic blocks, conditional sections by data availability, supplementary content (related items, tips, user-generated content).
- **URLs**: one clean pattern per page type; breadcrumbs and BreadcrumbList schema from the URL hierarchy.
- **Internal linking**: hub/spoke (category hub → programmatic pages), 3–5 related links per page by shared attributes, descriptive varied anchors.
- **Thin-content gates** (hard rules):
  - < 40% unique content per page → flag as thin (penalty risk).
  - < 300 words per page → flag for review.
  - 100+ pages without content review → warning, audit before publishing.
  - 500+ pages without justification → hard stop: explicit user approval plus a thin-content audit.
  - ≥ 30–40% of content must be genuinely unique between any two pages — not just city/keyword string replacement.
  - Human review of a 5–10% sample before publishing; progressive rollout in batches of 50–100 pages, monitor indexing and rankings 2–4 weeks before expanding. Never publish 500+ programmatic pages at once without explicit quality sign-off.
  - Standalone value test: "Would this page be worth publishing even if no other similar pages existed?" If no, do not publish it.
- **Index bloat**: noindex low-value pages; consolidate true duplicates with canonicals; reserve noindex/canonical for filtered views that are genuinely low-value; monitor crawl stats above 10k pages.

## E-commerce SEO
Product-page checklist (title, meta, headings, images, internal links, unique description, specs, reviews) scored: schema completeness 25%, title and meta 15%, image optimisation 20%, content quality 20%, internal linking 10%, technical 10%. Shopping intelligence (Google Shopping, Amazon) is paid DataForSEO work — cost guardrail applies. Never present a competitor's price as the user's price; verify from the merchant's own page.

## SXO (search experience optimisation)
When a page ranks but does not convert, the problem may be intent or layout, not keywords. Pipeline: acquire the target → analyse the SERP backwards (what page type dominates? what do the ads, PAA, and AI Overview say the user wants?) → detect page-type mismatch (a blog post where the SERP wants product pages is CRITICAL) → derive user stories from PAA, ad themes, related searches, snippet format, AI Overview → gap-score the page (page type, depth, UX, schema, media, authority, freshness) → score against personas (relevance, clarity in 10 seconds, trust, action) → optional wireframe (current vs target). Hand content findings to the content workflow and layout findings to the design workflow — SXO diagnoses, it does not redesign.

## FLOW framework (evidence-led SEO)
Find → Leverage → Optimise → Win, plus a Local stage. Find: keyword research, gap analysis, SERP intent mapping. Leverage: backlink strategy, off-site authority. Optimise: pick the 2–3 most relevant prompts/checks for the context (industry vertical, prior audit findings, URL signals) — never run all of them. Win: bottom-of-funnel, conversion, dual-surface scorecard. Local: GBP, meta, title tags, local audits. FLOW is a way to order the work in this skill, not a separate audit — its stages map onto the workflows above.

## Drift monitoring
Baseline (title, meta description, canonical, robots directives, H1/H2/H3, JSON-LD, OG tags, Core Web Vitals, status code, HTML hash, schema hash) → compare on change → severity: CRITICAL (SEO-breaking, act now), WARNING (investigate within a week), INFO (awareness, may be intentional). Cross-reference findings: schema removed → run the schema check; CWV regression → technical audit; title/meta changed → page analysis; noindex added → crawlability audit; status changed to error → full technical pass. A baseline is "known good" only because the user said so.

## Site-quality gate (from web-quality-audit)
A fast pre-flight that complements the SEO audit — performance, accessibility, SEO basics, best practices:
- **Performance**: LCP < 2.5s, INP < 200ms, CLS < 0.1; compress images (WebP/AVIF, srcset); minimise and split JavaScript; critical CSS; `font-display: swap`; preconnect/preload critical origins and assets; lazy-load below-fold content; long cache TTLs for static assets.
- **Accessibility**: meaningful alt text (decorative images `alt=""`); contrast 4.5:1 normal text, 3:1 large (WCAG AA); never colour alone; captions/transcripts; full keyboard access with visible focus and skip links; page `lang`; labelled form inputs with described errors; valid HTML, ARIA used correctly (native elements first).
- **SEO basics**: valid robots.txt, XML sitemap in Search Console, canonicals, no noindex on important pages, unique titles (50–60 chars), meta descriptions (150–160), single H1 with logical headings, descriptive link text, mobile-friendly (tap targets ≥ 48px), HTTPS, structured data.
- **Best practices**: HTTPS, no console errors, no deprecated APIs, no intrusive interstitials. This gate is a checklist, not a score — it finds the obvious fast; the full audit finds the rest.
