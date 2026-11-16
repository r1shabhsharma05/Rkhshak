# WCAG Checklist — accessibility, concrete criteria

Accessibility is not a vibe. WCAG 2.2 gives concrete numbers. This is the checklist version — run it on every screen before ship.

## The numbers that matter
| Rule | Criterion | Pass means |
|---|---|---|
| Text contrast | 4.5:1 | Normal text vs its background is at least 4.5:1. Large text (18pt+ / 14pt+ bold) at least 3:1. |
| UI contrast | 3:1 | Buttons, icons, input borders, focus indicators vs their background are at least 3:1. |
| Touch target | 24×24px min | Every clickable target is at least 24×24 CSS px (WCAG 2.2 AA). 44×44 is better. |
| Focus visible | 2.4.7 | Every interactive element shows a visible focus indicator when tabbed to. Never `outline: none` without a replacement. |
| Keyboard | 2.1.1 | Everything clickable is reachable and operable by keyboard alone. No keyboard traps. |
| Alt text | 1.1.1 | Every meaningful image has alt text that says what it shows. Decorative images have empty alt (`alt=""`). |
| Headings | 1.3.1 / 2.4.6 | One H1 per page, headings in order (no skipping H1 → H3), headings describe the section. |
| Labels | 1.3.1 / 3.3.2 | Every input has a visible label (not placeholder-only). Errors are identified in text, not just colour. |
| Colour alone | 1.4.1 | Colour is never the only way information is conveyed. Errors have an icon + text, not just red. |
| Reduced motion | 2.3.3 | Animations respect `prefers-reduced-motion` — no flashing, no parallax, no auto-playing motion for users who asked for less. |
| Reflow | 1.4.10 | At 320px wide, no horizontal scroll, no content cut off. |
| Zoom | 1.4.4 | At 200% zoom, everything still works and nothing overlaps. |

## How to test (no special tools needed)
1. **Keyboard only:** unplug the mouse. Tab through the whole page. Can you reach everything, see where you are, and do the task?
2. **Zoom 200%:** does anything overlap or disappear?
3. **Contrast check:** run a contrast checker on every text/background pair (browser devtools has one built in).
4. **Screen reader pass:** turn on VoiceOver / TalkBack / NVDA for 5 minutes. Does the page make sense when read aloud? Do buttons announce what they do?
5. **Colour off:** view the page in greyscale. Is every error, success, and status still clear?

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Text contrast ≥ 4.5:1, UI contrast ≥ 3:1 | Any pair below the ratio |
| 2 | Full task completable by keyboard alone, focus always visible | A button, link, or input unreachable by keyboard, or focus invisible |
| 3 | Every image has alt (or empty alt if decorative) | A meaningful image with no alt |
| 4 | Headings in order, one H1 | Skipped heading levels or no H1 |
| 5 | Every input labelled, errors in text not just colour | Placeholder-only labels or colour-only errors |
| 6 | Touch targets ≥ 24px, no horizontal scroll at 320px | Tiny targets or sideways scroll on a phone |
| 7 | Reduced motion respected | Animation plays for users who asked for less |
| 8 | Screen reader pass: page makes sense read aloud | Buttons announce nothing, or the order is nonsense |

## How this maps to the design gate
Accessibility is a gate, not a polish step. A screen that fails any row above fails the Design Gate — same as a screen that fails the Floor. Fix it before ship, don't file it as "later".
