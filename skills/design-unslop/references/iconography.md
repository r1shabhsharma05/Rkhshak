# Iconography — a consistent icon system

Icons are a language. If every icon speaks a different dialect, the interface is noise. One system, used the same way everywhere.

## Rules
- **One icon set.** Pick one set (Lucide, Heroicons, Material, or a custom set) and use it everywhere. Mixing sets is the fastest way to make a UI look assembled from parts.
- **One stroke, one weight.** All icons share the same stroke width and the same visual weight. A thin icon next to a thick icon looks broken even if both are "correct".
- **24px grid.** Icons are drawn on a 24×24 grid and used at 16, 20, or 24px. Never stretch an icon, never use one at a random size.
- **Meaningful, not decorative.** An icon must mean something. If the user can't tell what it does without the label, the icon failed — add the label, or pick a better icon.
- **Labels with icons for actions.** A button that does something important carries a label + an icon, not an icon alone. Icon-only buttons are for universal actions (close, search, menu) and they get a tooltip + an accessible name.
- **No emoji as icons.** Emoji render differently on every platform and mean different things in different cultures. Use a real icon.
- **Custom icons only when the set has no answer.** If the product needs an icon the set doesn't have, draw one in the same style (same grid, same stroke). One custom icon that matches beats ten that don't.
- **States are visible.** An active icon looks different from an inactive one (filled vs outlined, or a colour change) — not just a 5% opacity shift nobody can see.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | One icon set used everywhere | Two or more sets mixed on one screen |
| 2 | Same stroke width + visual weight across icons | A thin icon next to a thick one |
| 3 | Icons on a 24px grid, used at 16/20/24px | Stretched or random-size icons |
| 4 | Every action icon is understandable (label or universal) | An icon nobody can identify |
| 5 | Important actions have label + icon | Icon-only button for a non-universal action |
| 6 | No emoji used as icons | An emoji standing in for an icon |
| 7 | Active/inactive states visibly different | State change invisible at a glance |
