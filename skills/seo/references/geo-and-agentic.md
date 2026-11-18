# GEO and agent readiness

## GEO: being cited by AI search
GEO (Generative Engine Optimization) and AEO (Answer Engine Optimization) ask a different question from classic SEO: not "does this rank?" but "does an answer engine quote this?" The overlap is real — good content helps both — but the checks differ.

### Citability score (the core)
- **Factual density**: specific facts, statistics, dates, and data an engine can cite. Vague claims are un-citable.
- **Clear claims**: the page's core argument stated plainly at the top, in one or two sentences.
- **Structured answers**: question-answer formats, definition patterns, step-by-step instructions.
- **Source citation**: the page cites authoritative external sources for its claims.
- **First-party data**: original research, statistics, case studies, unique datasets — the most-cited material in citation studies.
- **Entity clarity**: brand, authors, and key concepts named clearly and consistently, backed by Organization and Person schema.
- **Author and trust signals**: named authors with credentials, an About page that says who runs the site, contact information, testimonials, awards, press mentions.
- **Comprehensiveness**: the topic fully addressed, not half-answered.
- **Originality**: a point of view, original data, or a unique perspective — the thing an engine prefers to cite over the tenth rewrite.

### Brand signals
Citation studies consistently find brand mentions correlate with AI citations more strongly than backlinks do. YouTube mentions, community mentions, and a Wikipedia presence are strong signals; domain authority alone is weak. The honest version of this: become worth mentioning — original data and a clear position — rather than chasing mention counts.

### Recency
In one large citation study, content updated within 3 months was cited about 3 times more often. That is a correlation; no AI search system documents a staleness cutoff. Refresh pages whose facts changed; never fake freshness by changing a date.

### AI crawler table
See `technical.md` for the full table. The rule that matters here: check the right bot for the claim. GPTBot is training-only; OAI-SearchBot decides ChatGPT Search citability; Google-Extended is training and grounding, not Search inclusion. Blocking the wrong bot and claiming a visibility win is a self-inflicted error.

### What GEO is not
- Not a separate sitemap, not a magic file. `llms.txt` helps agents find content; it does not make content citable.
- Not a ranking guarantee. No one can promise citation; report citability gaps and what would close them.

## Agent readiness
Audit whether AI agents can use the site, not just read it:
1. **Lighthouse Agentic Browsing score** (X/N, mobile and desktop): the headline number.
2. **Accessibility tree**: accessible names, valid roles, nothing interactive hidden from the tree. If an agent cannot see the control, the control does not exist for it.
3. **Primary content without JavaScript**: server-rendered. An agent that does not run JS gets the page or it does not.
4. **robots.txt**: reachable, with deliberate groups per AI purpose (training, search, user-triggered agents). Private paths are protected by authentication, not by robots.txt — user-triggered agents may ignore it.
5. **Content-Signal**: inside every relevant robots group. Absence is information; a gap is a warning.
6. **llms.txt**: passing the Lighthouse rules. Absence is information, not a failure.
7. **Markdown delivery**: `.md` URLs or `Accept: text/markdown` with `Vary: Accept`.
8. **WAF behaviour** (only with authorisation): verified bots and signed agents get through; no CAPTCHA on content.
9. **WebMCP tools** (transactional sites): imperative tools bound to existing handlers, registered where agents look.
10. **Discovery files**: `/.well-known/` entries (API catalog, OAuth metadata, agent card) only where the site actually runs those things.
11. **Real 404s**: unknown URLs return a real 404. A catch-all 200 fails llms.txt and discovery checks.

### Priorities
P0: accessibility tree, CLS ≤ 0.1, content without JS, robots.txt reachable with deliberate groups, WAF lets verified agents through. P1: auth-not-robots for private paths, Content-Signal, llms.txt, Markdown delivery, stable confirmation states (no hover-only menus or focus traps). P2/P3: WebMCP registration, API catalog, agent cards — only where the site runs them.

### Honest reporting
Every dated claim (a vendor's support status, a model name, a threshold) is re-verified before it is repeated — standards in this area move monthly. If a check could not be run (no Lighthouse access, no WAF logs), say so in the report rather than scoring it as a pass.
