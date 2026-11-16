# Design Tokens — colors, spacing, type, radius, shadow as code

A design system that lives only in Figma drifts. Tokens are the design system as code: named values that every screen reads from, so a change in one place changes everywhere — and nothing drifts.

## What a token is
A named value, not a raw number. `color.primary` not `#3B82F6`. `space.md` not `16px`. `radius.card` not `8px`. The name says what it's for; the value is the implementation.

## The token sets
### Color
- **Semantic, not literal.** `color.text`, `color.text-muted`, `color.background`, `color.surface`, `color.border`, `color.primary`, `color.success`, `color.warning`, `color.error` — not `blue-500` or `grey-300`. When the palette changes, the names stay.
- **One primary, one accent.** Everything else is neutral. A screen with five competing colours has no hierarchy.
- **Dark mode is a second value per token**, not a second design. `color.background` is white in light mode, near-black in dark mode. The component doesn't change; the token value does.

### Spacing
- One scale: `space.xs: 4`, `space.sm: 8`, `space.md: 16`, `space.lg: 24`, `space.xl: 32`, `space.2xl: 48`, `space.3xl: 64`. Every margin, padding, and gap uses these. (See `references/layout-grid.md`.)

### Type
- One scale: `text.xs` through `text.2xl`, each with a size + line-height + weight. Body text is one size, everywhere. Headings step up the scale, never a random size.
- **One font family (two at most).** Body + headings share a family, or headings get a display family. Three families is a finding.

### Radius + shadow
- **Radius scale:** `radius.sm: 4`, `radius.md: 8`, `radius.lg: 16`, `radius.full: 9999`. Cards use one radius, buttons another — consistently.
- **Shadow scale:** `shadow.sm` (subtle lift), `shadow.md` (card), `shadow.lg` (modal). No more than three levels. A shadow that doesn't mean anything is decoration.

## Rules
- **No raw values in components.** A component that says `16px` or `#3B82F6` is bypassing the system. Lint for it.
- **Tokens live in one file.** One source of truth (`tokens.css`, `theme.ts`, `design.json`). A token defined in two places will drift.
- **Changing a token is a design decision.** It changes every screen that uses it — review it like a design change, not a code tweak.
- **Name for purpose, not appearance.** `color.error` not `red`. `space.section` not `48px`. When the look changes, the name still makes sense.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | No raw values in components (all from tokens) | `16px` or `#3B82F6` hardcoded in a component |
| 2 | One token file, one source of truth | Tokens defined in two places |
| 3 | Semantic color names (text/background/primary/error) | Literal names (`blue-500`) driving the UI |
| 4 | One spacing scale, one type scale, one radius scale | Random sizes across screens |
| 5 | Dark mode is a second value per token | A second design for dark mode |
| 6 | One font family (two max) | Three or more families |
| 7 | Shadow scale has ≤ 3 levels, each meaningful | Shadows everywhere with no system |
