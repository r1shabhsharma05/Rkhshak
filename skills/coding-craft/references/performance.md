# Performance — measure, fix the bottleneck, prove it, guard it

Distilled from the performance-optimization skill (MIT) and its `optimization-patterns.md`. Method in our own words; the full workflow and targets live in that source. Use when performance requirements exist, when a regression is suspected, or when Core Web Vitals are failing.

## The workflow
1. **Measure.** Establish the baseline with a real measurement — a profile, a timing, a Lighthouse run — before changing anything. A fix without a before-number is a guess. Log where to start measuring (the slowest interaction, the largest page, the worst query), not everywhere at once.
2. **Identify the bottleneck.** One bottleneck at a time: the profile says where the time goes. The usual suspects are network (too many requests, too much payload), rendering (layout and paint work), and data (unindexed queries, N+1 loads). Pick the biggest one.
3. **Fix the bottleneck.** Only the bottleneck. An optimisation anywhere else is motion, not progress.
4. **Verify (keep or revert).** Measure again, the same way. If the number did not improve, revert the change — do not keep an optimisation that does not optimise. Log every attempt, including the reverted ones, so the next person does not retry them.
5. **Guard against regression.** A performance budget in CI (bundle size check, Lighthouse CI, query-time check) so the regression is caught by a machine, not by a user.

## Core Web Vitals targets
Largest Contentful Paint, Interaction to Next Paint, and Cumulative Layout Shift each have a "good" threshold; the exact numbers live in the source and in the platform docs — quote the current threshold, never a remembered one. If a target is missed, the workflow above is how it is fixed, not a checklist of tricks.

## Rationalizations — do not accept these
- "It feels fast enough" — feelings are not measurements.
- "We optimised the wrong thing, but it is still better" — an unmeasured improvement is not an improvement.
- "Performance work can wait until launch" — by launch it is a rewrite, not a fix.

## Red flags
- Optimising without a profile.
- A "fix" kept despite a flat or worse measurement.
- A regression discovered by users instead of by the budget check.
