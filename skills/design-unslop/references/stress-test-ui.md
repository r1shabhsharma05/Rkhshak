# Stress-Test UI — break it with worst-case data

Distilled from the break-ui method (in our own words). Use when a component or screen must survive real data: long names, missing fields, extreme numbers. A design that only works with its demo content is not finished.

## Workflow
1. **Map the surface.** List every place the screen shows data it does not control: names, emails, titles, counts, dates, prices, images, user-generated text. Note which fields can be empty, which can be very long, and which come from another system.
2. **Build the worst case.** One dataset per screen, containing all of these at once: a very long name (60+ characters), a one-letter name, an unbreakable email address, a missing avatar, a missing optional field, zero items, one item, a huge count (1,000,000+), a long label, non-Latin text, emoji in a name, an extreme number, a broken image URL.
3. **Wire the toggle.** Put the worst case behind a visible "Demo data / Worst case" toggle so anyone can switch between real data and the stress set. The toggle is part of the deliverable, not a throwaway.
4. **Break it.** Render every state with the worst case on and record everything that broke, with the fix for each. Then fix on request — the report comes first, the fixes second.

## Failure signatures (what to look for)
- Text overflowing its container, clipped mid-word, or pushing siblings off-screen.
- Layouts that grow without bound (a card that becomes a page, a table that never ends).
- Empty states that show a broken shell (headers with no content, buttons to nothing).
- Counts that wrap, overlap, or lose their unit ("1,000,000" colliding with its label).
- Images that fail and leave a hole with no fallback (alt, initials, or a neutral block).
- Truncation that hides the only distinguishing information (two items that truncate identically).

## Truncate, wrap, or clamp — decide per field
- **Truncate** (with ellipsis + full value on hover/focus) when the field is a label and the full value is available elsewhere.
- **Wrap** when the field is content the user must read in full (messages, descriptions).
- **Clamp** (N lines, then ellipsis) when the field is a preview and the full value is one tap away.
- Never truncate the only copy of a value the user needs to act on (an email address, an amount, a code). Never truncate two different values to the same visible string.

## Report format
- **What broke** — one line each: where, with what data, what the user sees.
- **Decisions for you** — cases with no single right answer (truncate vs wrap on a given field), as a shortlist for the user to pick.
- **What held up** — the parts that survived the worst case, so the next run knows what not to re-break.

## Rules
- The worst case is built from the product's real field shapes, not invented data types.
- A fix that only works for the demo data is not a fix — re-run the toggle after every fix.
- Never ship a screen whose empty state, error state, and longest-content state have not been seen.
