# Design Regression — compare runs over time (before / after)

A single design pass is a snapshot. A skill that tracks regressions is useful over time. Compare every new run against the previous run and report what changed.

## How it works
1. **Keep every DESIGN-AUDIT.md + screenshot.** Store each run's audit (date, screen, counts) and its before/after screenshots in the repo or a runs folder. Never overwrite the previous run.
2. **Carry forward open items.** Every item that was open in the previous run stays open in the new run unless fresh evidence (a new screenshot at the same size) shows it fixed. A fix claim without fresh evidence does not close an item.
3. **Classify each item in the new run:**
   - **New** — not in the previous run (new screen, new tell, or newly discovered).
   - **Fixed** — was open, now passes with fresh evidence (screenshot at the same size).
   - **Regressed** — was passing, now fails (a change broke it — e.g. a new feature reintroduced a purple gradient, a refactor broke the responsive layout).
   - **Still open** — was open, still open.
   - **Waived** — was open, user accepted it in writing (record reason + expiry).
4. **Report the delta first.** The new run's report opens with the delta: X new, Y fixed, Z regressed, W still open. A regression is a Critical-priority item — it means a fix or feature broke a previously passing design.
5. **Never claim "all fixed" without a full re-run.** A fix round fixes listed items; only a full re-run of every checklist proves the gate. A partial re-run (only the fixed items) is not a gate pass.

## Before / after (the proof)
- Every run stores a **before** screenshot (the screen as found) and an **after** screenshot (the screen as shipped), at the same size and breakpoint.
- Compare them side by side at the same size. Name the gap in one line per change ("hero: gradient removed, headline cut from 14 words to 6").
- If a before/after pair is missing, say so in the report — never imply a run is regression-free without the screenshots.

## What to store per run
- Date, screen/route, breakpoint(s) checked.
- Counts: Tells found · fixed · still open · waived · N/A.
- The item list with severity + status (new / fixed / regressed / still open / waived).
- The delta vs the previous run + the before/after screenshots.

## When to compare
- Every run, automatically. If no previous run exists, say so in the report — never imply a first run is a regression-free run.
