# Dark Mode — rules (not just "check it")

Dark mode is a second design, not a filter over the light one. If the product has dark mode, it must pass this checklist. If it doesn't, say so explicitly — never ship a broken dark mode.

## Surfaces (the core rule)
- Depth comes from **surface steps + hairlines, not shadows**. Raise a surface by lightening it one step, not by adding a shadow.
- Build a surface ramp: background → raised → overlay → highest. Each step is a small, deliberate lift (e.g. +4–8% lightness). Never pure black (#000) as the background — near-black (#0A0A0A–#121212) reads better and lets surfaces step up.
- Borders are quiet hairlines (text color at 6–10% opacity). Never bright borders.
- A window or object floating over an image may keep a soft neutral shadow. Nothing else gets a shadow.

## Color
- The accent is often too bright in dark mode. Darken the accent for text/ink use, or use a lighter tint for fills — the accent must still reach 4.5:1 as text.
- Semantic colors (green/red/amber) are toned down to sit inside the palette — never neon.
- The primary button can be an off-white from the ramp with dark text. This often looks more deliberate than a colored button.
- Images/photos keep their own light — don't dim them with an overlay unless the text over them needs it (then use a scrim, not a global dim).

## Text
- Text roles stay three (primary, secondary, muted) — but the values change. Muted text in dark mode must still reach 4.5:1 (muted greys on dark backgrounds fail contrast more often than on light).
- Pure white (#FFF) text on near-black is harsh for long reading. Use off-white (#EDEDED–#F5F5F5) for body text.

## What to check
- Every screen in both modes (not just the home screen). Toggle the mode and re-walk the screen.
- Charts: each series is still distinguishable (hue + marker/pattern, not hue alone).
- Logos: third-party logos keep their real colors; if a logo is dark-on-transparent and disappears on dark, use its light variant (never invert it yourself).
- The mode toggle itself is findable and its state is clear. Respect the system preference by default (`prefers-color-scheme`).
- Reduced motion + dark mode together: both must work at the same time.
