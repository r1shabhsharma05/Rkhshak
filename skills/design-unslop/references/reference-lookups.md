# Reference Lookups — search a design-intelligence index before deciding

Distilled from the ui-ux-pro-max method (searchable local data: styles, product palettes with reasoning, font pairings, UX guidelines, icons, animation presets, chart types, stacks). The data itself is not copied here — this file is the method for using any such index. Use when a decision (palette, type pairing, pattern, chart, stack rule) should come from researched examples rather than from habit.

## The index (what to look up, by decision)
| Decision | Look up |
|---|---|
| Palette | Product palettes + the reasoning behind each (why these colours, for what product, what breaks if you swap one) |
| Type | Font pairings (display + text, with the pairing's character) |
| Pattern | UX guidelines with rationale (the rule, why it exists, the failure it prevents) |
| Icons | The icon set's grid, stroke, and naming — one set per product |
| Motion | Animation presets with their timing values (do not re-derive curves by hand) |
| Charts | Chart types by question (which chart answers which question — see also `data-viz.md`) |
| Stack | Stack-specific UI rules for the framework in use |

## Query contract
1. **One dominant intent per query**, 2–5 meaningful terms plus one useful constraint (product, platform, interaction). Never a vague whole-page query.
2. **New project/page or system-wide direction** → generate the design system first (palette + type + spacing + radius + motion tokens), then supplement with targeted searches.
3. **Targeted concern or component bug** → one explicit domain (palette, type, icons, ux, chart, stack).
4. **Known implementation stack** → the stack search first; add a separate domain search only for a distinct design concern.
5. **Verify before applying.** Check the returned result's identity, domain, and fit for this product and platform. A result for the wrong product or platform is not a result.
6. **Retry once** with a narrower rewrite or an explicit domain when output is empty or off-topic. If the retry fails, state that no verified match was found and label any general guidance as a fallback.
7. **Do not persist unverified output.** Nothing from a lookup enters the locked design system (`design.md`) until it has been checked against the product.

## Accessibility lookups (one outcome at a time)
Search the observable outcome first (`error summary validation`, `focus not obscured`, `dragging movements`, `accessible authentication`), then a component-specific domain if needed (`decorative icon aria hidden`, `icon button accessible label`). Do not accept a generic accessibility result for a specific interaction or WCAG criterion.

## Rules
- A lookup informs the decision; it does not make it. The direction and the Floor still decide.
- Palettes and pairings are starting points with reasoning attached — take the reasoning, re-derive the values for this product, never paste a palette because it ranked first.
- If the index has no entry for the decision, say so. An absent result is information, not a licence to guess.
