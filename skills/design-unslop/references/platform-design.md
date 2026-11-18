# Platform Design — design review grounded in platform guidelines

Distilled from Apple's Human Interface Guidelines (as summarised in the apple-design skill: 123 pages of HIG material, including 57 component pages) and the classic HIG heritage. Method in our own words; guideline names are cited, wording is not copied. Use when auditing, reviewing, or improving a mobile or desktop app design — native or cross-platform (Flutter, React Native, Tauri, Electron). Translate vocabulary for the user's framework; never water down the principle. A web app or an Android-only app gets the principles and the foundations (accessibility, colour, typography, navigation), not the iOS-only component rules.

## The eight principles (first filter)
A screen that breaks a principle has a bigger problem than any single guideline it breaks. Test each one before opening any component page:
1. **Clarity** — the interface says what it is and what it does; nothing decorative competes with content.
2. **Deference** — the UI defers to content; chrome stays quiet.
3. **Depth** — layers and motion convey hierarchy and spatial relationships, not decoration.
4. **Consistency** — the same thing looks and behaves the same way everywhere; platform conventions are followed unless there is a reason not to.
5. **Direct manipulation** — people touch the content itself, not a proxy for it.
6. **Feedback** — every action acknowledges itself, immediately.
7. **Forgiveness** — destructive or irreversible actions are hard to do by accident and easy to undo.
8. **Delight** — craft in the details, earned after the first seven hold.

## Review process: five lenses, in this order
1. **Accessibility (failures are Critical).** Contrast, touch target size, VoiceOver/screen-reader labels, Dynamic Type scaling, reduced motion. An inaccessible screen fails the review regardless of how it looks.
2. **Platform conventions (usually High).** Navigation structure, tab bars vs sidebars, sheets vs modals, system controls used where the platform provides them. A custom control that replaces a system one must be better in a way a user can feel.
3. **Visual design and craft (High or Medium).** Type scale and optical sizing, colour roles, spacing, icon consistency, imagery honesty.
4. **Interaction (usually Medium).** Gestures have visible alternatives; drag, swipe, and long-press are discoverable; states are complete.
5. **Content and writing (usually Medium).** Short, plain, specific; no invented proof; errors say what happened and what to do next.

For each finding: the principle or guideline behind it (cited as the HIG section), the severity, and the fix. A review that lists only surface findings without the principle behind each one has not been done.

## Liquid Glass (translucent material)
- Liquid Glass, or any blur, belongs only on the floating functional layer (bars, sheets, floating controls) — never in content, never as a page background.
- Legibility comes first: content behind the material must stay readable at every scroll position; if it does not, the material is wrong for that spot, not the content.
- One material per screen. Mixing glass, solid, and blur in different places reads as three products.
- Never use translucency to hide weak layout. A blurred bar over a bad grid is still a bad grid.

## Platform notes
- **iPhone Duo / foldables:** layouts must adapt to a second screen or a fold — no content hidden behind the hinge, no interaction that assumes one fixed width. Code that blocks adaptation is a finding, not a constraint.
- **Dark mode:** a real second palette, not an inverted light mode. Surfaces, text, and the accent are re-chosen; translucent materials are re-tested.
- **Apple Pay buttons and marks:** use the system-provided button and mark, drawn exactly as supplied. Never hand-draw a payment button or a brand mark.
- **Widgets:** glanceable, one job, no scrolling inside the widget, deep-link to the app for the rest.
- **Heritage (why a guideline exists):** the classic HIG editions repeat the same rules of thumb — put the user's content first, make the frequent things fast, make the dangerous things hard. When a current guideline and an old one disagree, the current one wins; the old one explains the intent.

## Working rules
- Load the platform's own guidance before reviewing; do not review from memory.
- A cross-platform app follows the platform it is on for navigation, gestures, and system controls, and keeps its own brand only in content, colour, and type.
- Never redesign a screen the user did not ask to change; a review stops at findings and the three changes that would move the screen most.
