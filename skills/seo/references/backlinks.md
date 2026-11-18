# Backlinks

## Data sources (cheapest first — never pay before the free tier is exhausted)
1. **Common Crawl** (always available): domain-level link graph with PageRank-style signals.
2. **Verification crawler** (always available): checks whether a known backlink still exists on the source page.
3. **Moz API** (free signup), **Bing Webmaster** (free signup), **Keywords Everywhere** (free signup; domain rank plus referring-domain count).
4. **DataForSEO** (paid — cost guardrail applies, see `live-data.md`).

A link is only counted when verified: read the source page's `rel` attributes and page-level nofollow before calling it followed. Statuses: `verified` (link found), `link_removed` (page loads, no link), `unverifiable_js` (JS-rendered — report as unconfirmed, not removed), `lost` (source page 404/410).

## Profile overview
| Metric | Good | Warning | Critical |
|---|---|---|---|
| Referring domains | > 100 | 20–100 | < 20 |
| Follow ratio | > 60% | 40–60% | < 40% |
| Domain diversity | No single domain > 5% | One domain > 10% | One domain > 25% |
| Trend | Growing or stable | Slow decline | Rapid decline (> 20%/quarter) |

## Anchor text distribution
| Anchor type | Target range | Over-optimisation signal |
|---|---|---|
| Branded (company/domain name) | 30–50% | < 15% |
| URL / naked link | 15–25% | — |
| Generic ("click here", "learn more") | 10–20% | — |
| Exact-match keyword | 3–10% | > 15% |
| Partial-match keyword | 5–15% | > 25% |
| Long-tail / natural | 5–15% | — |

An exact-match share above 15% is an over-optimisation signal, not a win — say so plainly, with the number.

## Referring-domain quality
- TLD distribution: .edu, .gov, .org lean high-authority; a heavy .xyz / .info share leans low-quality.
- Country distribution: should match the target market. 80%+ from irrelevant countries is a private-blog-network signal.
- Authority tiers: a healthy profile has links from all tiers, not only one.
- Follow/nofollow per domain: sites that only ever nofollow pass limited value.

## Toxic link detection
Flag: links from known spam / link-farm / hacked pages, sitewide footer links from unrelated sites, sudden spikes of low-quality domains, exact-match anchors from irrelevant pages. Disavow is a last resort, not a first step — recommend it only with the evidence attached, per-link, and only after the user understands it is a request to Google, not a deletion. Never disavow a link the user earned.

## Competitor gap analysis
Compare the target's referring domains against each competitor's: domains linking to competitors but not to the target, grouped by whether they are realistically earnable (resource pages, directories, press, partners) versus not (their own properties, paid placements). A gap list is a prospect list, not a to-do list — rank it by earnability.

## New and lost backlinks
Track over time (see drift in `plan-and-scale.md`): new links worth keeping, lost links worth reclaiming (contact the source when the link was editorial and the page still exists).
