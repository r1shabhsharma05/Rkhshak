# Accessibility Checklist — the a11y gate

A design that some people can't use is not done. Run this checklist on every screen. Zero Critical/High is required for the Design Gate to pass.

## Contrast (Critical if failed)
- Body text: **4.5:1** minimum against its background.
- Large text (18px+ or 14px+ bold): **3:1** minimum.
- UI components and meaningful graphics (icons, borders that convey state, focus indicators): **3:1** minimum.
- Check contrast over images and gradients too, not just solid backgrounds. Text over a photo needs a scrim or a calm area behind it.
- Never rely on color alone to convey meaning (error = color + icon + text, not color only). Check the design in grayscale: if meaning disappears, it fails.

## Keyboard (Critical if failed)
- Every interactive element is reachable by keyboard (Tab order follows the visual order).
- Every interactive element has a visible `:focus-visible` state, appearing instantly, inside the palette.
- No keyboard traps (focus can always leave a modal, menu, or dialog with Esc / Tab).
- Skip link exists on pages with navigation ("Skip to content").
- Modals trap focus while open and return focus to the trigger when closed.

## Screen reader
- Every image has alt text (meaningful images describe their content; decorative images have empty alt).
- Every icon-only button has an accessible name (aria-label).
- Headings follow a logical order (one H1, then H2, H3 — never skip levels, never use a heading for styling).
- Form inputs have visible labels (not placeholder-only). Errors are announced and linked to the field.
- Status changes (loading done, item added, error) are announced (live regions), not silent.
- Decorative split text (staggered headings) hides the split words from assistive technology and keeps the unsplit content visible.

## Color-blind safety
- Check the palette for the three common types (protanopia, deuteranopia, tritanopia). If two states are only distinguishable by hue (e.g. red vs green), add an icon, label, or pattern.
- Charts: each series has a distinct hue AND a distinct marker/pattern, or a direct label.

## Motion
- Every animation has a `prefers-reduced-motion: reduce` fallback. Under reduced motion, render final states immediately — never merely shorten the animation.
- No auto-playing motion that can't be paused (carousels, videos, parallax). No flashing content (more than 3 flashes per second = seizure risk, never ship it).
- Content is visible with scripting off.

## Touch + target size
- Minimum touch target 44×44px (see `responsive-checklist.md`). This is an accessibility requirement, not just a responsive one.
