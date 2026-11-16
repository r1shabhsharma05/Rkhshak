# Design Self-Review — critique your own work before shipping

Before anyone else sees the design, review it yourself. This is the checklist that catches what the passes miss — the things that feel wrong but have no rule yet.

## The review (run in order, 10 minutes)
### 1. The 5-second test
Show the screen to someone (or to yourself after a break) for 5 seconds, then hide it. What do they remember? If it's not the one thing the screen is for, the hierarchy failed — the important thing isn't the biggest, or something else is shouting louder.

### 2. The squint test
Squint at the screen (or shrink it to a thumbnail). The structure should still read: one dominant thing, a clear order, no competing blocks. If it's a grey blur with no shape, the layout has no hierarchy.

### 3. Every state
Check loading, empty, error, and success for every component on the screen. A screen that only works when the data is perfect is a demo, not a product. The empty state is the most-seen state — design it first, not last.

### 4. The phone test
Look at it on a real phone, at arm's length, in daylight. If you can't read it or tap it, it fails — no matter how good it looked on a 27-inch monitor.

### 5. Read the copy out loud
Read every word on the screen out loud. If a sentence sounds like a press release, a template, or something no human would say, rewrite it. Copy that can't be spoken can't be understood.

### 6. Click everything
Click every link and button. Do they all go somewhere real? Does every one do what its label promises? A button that does nothing is worse than no button.

### 7. Remove one element
Delete the least important element on the screen. Does the screen get better? Then it stays deleted. Repeat until removing anything makes it worse. (This is the subtract-first pass, applied one last time.)

### 8. Compare to the direction
Read the 5-line direction again. Does the screen deliver it? If the direction says "the invoice total is the page" and the page shows a generic dashboard, the design drifted — go back to the direction, not forward to more polish.

### 9. Fresh eyes
If you built it, you can't see it. Show it to one person who hasn't seen it and watch them use it — don't explain, don't defend. Where they hesitate is where the design failed.

### 10. The honest verdict
Ask: would I be proud to show this to the person whose work I admire most? If not, name the one thing that embarrasses you most — and fix that one thing before anything else.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | 5-second test: the one thing is remembered | Visitor remembers decoration, not the purpose |
| 2 | Squint test: hierarchy reads at thumbnail size | Grey blur, no dominant element |
| 3 | Loading, empty, error, success states all designed | A state is missing or unhandled |
| 4 | Phone test at arm's length in daylight | Unreadable or untappable |
| 5 | Copy reads aloud like a person wrote it | Press-release or template sentences |
| 6 | Every link/button goes somewhere real and does what it says | A dead link or a misleading label |
| 7 | Remove-one-element test applied | An element exists that adds nothing |
| 8 | Screen matches the written direction | Design drifted from the direction |
| 9 | One fresh-eyes test done | Nobody outside the builder has seen it |
| 10 | Honest verdict: proud to show it | The builder names an embarrassment and ships anyway |
