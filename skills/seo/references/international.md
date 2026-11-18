# International SEO (hreflang)

## Validation checks (all must pass)
1. **Self-referencing tags**: every page points at itself in its own language/region.
2. **Return tags**: if A points at B, B points back at A. One-way hreflang is broken hreflang.
3. **x-default**: present when a fallback (language selector or global page) exists.
4. **Language codes**: ISO 639-1 two-letter codes (`en`, `de`, `fr`). `eng` is invalid.
5. **Region codes**: ISO 3166-1 Alpha-2 (`en-GB`, `en-US`, `de-DE`). `en-UK` is invalid — the region is `GB`, not `UK`.
6. **Canonical alignment**: hreflang lives on canonical URLs only, and canonicals agree across the language set.
7. **Protocol consistency**: all URLs HTTPS, trailing slashes matching the canonical exactly.
8. **Cross-domain**: allowed, but every domain's pages must carry the full return-tag set.

## Common mistakes
| Issue | Severity | Fix |
|---|---|---|
| Missing self-referencing tag | Critical | Add hreflang pointing to the same page URL |
| Missing return tags | Critical | Add matching return tags on all alternates |
| Missing x-default when fallback is required | Medium | Add x-default pointing to the fallback/selector page |
| Invalid language code (e.g. `eng`) | High | Use ISO 639-1 two-letter codes |
| Invalid region code (e.g. `en-uk`) | High | Use ISO 3166-1 Alpha-2 codes |
| Hreflang on a non-canonical URL | High | Move hreflang to the canonical URL only |
| HTTP/HTTPS mismatch | Medium | Standardise all URLs to HTTPS |
| Trailing-slash inconsistency | Medium | Match the canonical URL format exactly |
| Hreflang in both HTML and sitemap | Low | Choose one method (sitemap preferred for large sites) |
| Language without region when needed | Low | Add a region qualifier for geo-targeted content |

## Implementation methods
| Method | Best for | Pros | Cons |
|---|---|---|---|
| HTML link tags | Small sites (< 50 variants) | Easy, visible in source | Bloats `<head>`, hard to maintain at scale |
| HTTP headers | Non-HTML files (PDFs, images) | Works where HTML does not | Complex server config, not visible in HTML |
| XML sitemap | Large sites, cross-domain | Scalable, centralised | Not visible on page, needs sitemap maintenance |

## Generation process
1. Detect languages (URL path, subdomain, TLD, HTML `lang` attribute).
2. Map page equivalents across languages/regions — a page with no equivalent gets no hreflang entry, never a guess.
3. Validate every code against ISO 639-1 and ISO 3166-1.
4. Generate tags for each page including self-referencing.
5. Verify return tags are bidirectional.
6. Add x-default for the fallback page set.

## Content parity
Translated pages must be genuinely equivalent — a stub translation with hreflang pointing at a full page is a mismatch the search engine will notice. Where content genuinely differs by market (prices, regulations, availability), say so in the report rather than forcing parity. Machine-translated pages need a human QA pass before they carry hreflang; unreviewed machine translation is a quality risk, not a shortcut.
