# Typography + Color System — concrete scale and palette method

Pass 5 (type) and pass 2 (color) say what to do. This file gives the concrete numbers and the method to derive them — so the agent doesn't have to guess.

## Type scale (pick sizes from this scale, never one-offs)
| Role | Size | Weight | Line height | Use |
|---|---|---|---|---|
| Display | 48–72px | 500 | 1.05 | Hero headline only (one per screen). |
| H1 | 32–40px | 500 | 1.15 | Page title. |
| H2 | 24–28px | 500 | 1.25 | Section heading. |
| H3 | 20px | 500 | 1.3 | Subsection heading. |
| Body | 16–18px | 400 | 1.5–1.6 | Main text. Never below 16px. |
| Small | 14px | 400 | 1.45 | Captions, helper text, metadata. |
| Label | 14px | 500 | 1.4 | Form labels, buttons. Sentence case, never tracked capitals. |
| Mono | 13–14px | 400 | 1.5 | Figures, code, metadata (only if mono is the material). |

Rules: one interface family + at most one partner (display face OR mono, for one distinctive decision). Weights 400–500, 600 for rare emphasis. Hierarchy from size and color, never 800–900. Sentence case everywhere. `tabular-nums` + one number format. Negative tracking only on display sizes.

## Font pairing (how to choose)
- Choose type for the **character** (from the direction), not for trendiness. Calm + exact → a neutral grotesque. Warm + human → a humanist sans or a serif for display. Technical → a grotesque + mono.
- Keep the project's font when it is part of a real brand. A default nobody chose (e.g. Inter) may be swapped when another family fits the character better.
- Test the pairing at the smallest size it will be used. If the display face is unreadable at 20px, it is display-only.
- Load at most 2 families. Subset to the languages used. `font-display: swap`.

## Color system (derive the palette from the world — a method)
1. **Start with the world** (from the direction). Name the place/material: salt + charts + low light, ruled ledgers, paper + ink, maps + window light.
2. **Pick the neutral ramp.** Tint the neutrals toward the world (warm grey for paper, cool grey for instruments, green-grey for maps). Build 5–7 steps: background → raised → border → muted text → secondary text → primary text.
3. **Pick ONE accent from the world.** The accent is the one color that means "this product". Derive its hue from the world (coral from a tide table, ink blue from a ledger, leaf green from a garden). The accent covers a few percent of the screen.
4. **Add semantic colors only for meaning.** Green = good change, red = error, amber = warning. Tone them down to sit inside the palette. Never use them as decoration.
5. **Check the ramp:** three text roles only (primary, secondary, muted). Five lavenders means nobody chose. Every text role reaches 4.5:1 on its background.
6. **Test in grayscale.** If meaning disappears, the design relies on hue alone — add an icon, label, or pattern.

## Palette balance (per screen)
- Working screens (apps, dashboards): neutral surfaces, color in the content. The world shows in the accent, the charts, and the moments — not in the surfaces.
- Landing pages: surfaces can tint further toward the world, but the hero still has one accent and quiet chrome.
- Never: gradient text, colored glows, colored shadows, neon borders, blobs behind content, or a background that reads as a color (orange/brown/blue/green) on a working screen.
