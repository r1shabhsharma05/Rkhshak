# Layout + Grid — spacing scale, grid systems, composition

A layout is not "put things on the page". It's a system: a grid, a spacing scale, and a hierarchy. Without the system, every screen is a new decision — and every screen looks different.

## The grid
- **12 columns on desktop, 4 on mobile.** Everything aligns to the grid. A element that sits half a column off is visible even if nobody can name why.
- **One gutter, everywhere.** The gap between columns is the same on every screen (16px or 24px — pick one). A page with three different gutters looks assembled from parts.
- **Content width has a max.** Text columns cap at ~65 characters wide (around 700px). A paragraph that runs edge to edge on a wide monitor is unreadable.
- **Break the grid on purpose, never by accident.** A full-bleed image or a hero that spans the grid is a decision. An element that's 8px off the grid is a mistake.

## The spacing scale
- **One scale, powers of two (or a 4px base).** 4, 8, 16, 24, 32, 48, 64, 96. Every margin and padding comes from this scale. A random 13px margin is a smell.
- **Related things are close, unrelated things are far.** The gap between a heading and its paragraph is smaller than the gap between two sections. Spacing is meaning, not decoration.
- **Consistent rhythm.** The same section gap on every page. If one page uses 48px between sections and another uses 80px, the product feels inconsistent.

## Composition
- **One dominant thing per screen.** The most important element is the biggest, or the most contrasted, or the first thing the eye lands on. If two things compete, neither wins.
- **The 70% rule.** The important thing takes ~70% of the screen. The rest is frame. A screen where everything is the same size has no hierarchy.
- **F-pattern / Z-pattern.** People scan, they don't read. Put the important thing where the eye goes first (top-left for text, centre for a hero). Don't hide the action at the bottom of a long page.
- **Whitespace is not empty.** The space around an element is what makes it readable. Crowding is not density — it's noise.

## Alignment
- **Left-align text, always.** Centred paragraphs are hard to read (the eye has to find the start of every line). Centre only short headings and CTAs.
- **Align to something.** Every element aligns to an edge, a column, or another element. An element aligned to nothing is floating.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Everything aligns to a 12-col (desktop) / 4-col (mobile) grid | Elements half a column off |
| 2 | One gutter everywhere | Three different gutters on one page |
| 3 | Text columns cap at ~65 chars | Edge-to-edge paragraphs on a wide screen |
| 4 | Spacing comes from one scale (4/8/16/24/32/48/64/96) | Random margins (13px, 27px) |
| 5 | One dominant thing per screen (~70%) | Two things competing for attention |
| 6 | Text left-aligned (except short headings/CTAs) | Centred paragraphs |
| 7 | Every element aligns to an edge or a column | Floating elements aligned to nothing |
