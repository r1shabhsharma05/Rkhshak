# Design-System Lock — the design.md template

Once a design ships, lock the system in `design.md` at the project root. The next page reads it first and uses the same system — so consecutive builds don't drift back into slop. A locked system overrides the themes, shapes, and defaults below it. Pages share it.

## When to write it
After the first page/screen ships and passes the Design Gate. Say `lock the system` to create it. Update it whenever the system changes (new token, new component, new rule) — in the same change, not later.

## Template (copy this, fill every section)
```markdown
# Design System — <Product name>

## Direction
- **Product:** <one sentence: what it does, for whom>
- **Character:** <two or three concrete words>
- **World:** <the place/material the product belongs to>
- **Moment:** <the one or two places the screen gets its richness>
- **Signature:** <the one small detail only this product would have>
- **Concept:** <one sentence every choice can be checked against>

## Tokens
- **Neutrals:** <the ramp, tinted toward the world — list the steps>
- **Accent:** <the one accent, its hex, where it is used>
- **Text roles:** <primary / secondary / muted — hex + contrast>
- **Type:** <interface family + partner (if any) + their roles>
- **Spacing:** <4px grid, the scale used>
- **Radius:** <radius per nesting level>
- **Shadows/depth:** <one depth cue per surface — which one>

## Components
- <component>: <its states, its rules, where it is used>
- (list every component the product has — if it isn't listed, it doesn't exist yet)

## Rules (the Floor, as it applies here)
- <any Floor rule with a product-specific answer, e.g. "Hero: headline ≤7 words, one sentence, one action">
- <any waived Reflex, with its real reason>

## Do not
- <the tells this product must never have again, e.g. "Never a purple gradient, never emoji icons">
```

## Rules
- `design.md` is the source of truth. If a new page contradicts it, the page is wrong — fix the page, not the system (unless the user approves a system change, which updates `design.md` in the same change).
- Never invent a token, component, or rule that isn't in the shipped design. `design.md` describes what exists, not what would be nice.
- Keep it short. If it grows past one screen, split the component inventory into a separate file and link it.
