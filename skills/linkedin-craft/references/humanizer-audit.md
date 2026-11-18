# Humanizer audit — AI tells, emoji density, detector check (pre-publish)

Distilled from `linkedin-skills` (MIT bundle: humanizer — rewrite + audit
mode, folding in the former post-audit, emoji-detector, rules-explainer, and
detector-tester tools). Own words; reference files distilled, not copied.

## When to use
Reviewing a draft before publishing, removing AI tells, scoring AI emoji
density, defending a flagged rule, or running AI detectors in parallel.
**Run this before any draft is shown as final.** A draft that fails audit is
rewritten, not shipped.

## The audit (rewrite + `--mode audit` pre-publish review)
1. **AI-tell scan.** Flag every tell: emoji stacks; "excited to share";
   "in today's fast-paced world"; "leveraging / cutting-edge / game-changer";
   "delve / tapestry / landscape" filler; symmetrical triplets ("X, Y, and Z"
   as decoration); generic openers that could open any post; conclusions that
   restate the hook instead of landing a point.
2. **Emoji-density score.** Count emoji per post and per line. A stack of
   two or more in the hook, or emoji as bullet substitutes throughout, fails.
   One emoji, used once, where it adds meaning, is the ceiling for most drafts.
3. **Specificity check.** Every claim in the draft must trace to a real fact
   (story bank, user-stated) or a `[N]` placeholder. A specific-sounding
   sentence with no source is an invention, not a detail.
4. **Detector pass (optional, parallel).** Run the available AI detectors in
   parallel where configured; report each result. Detectors disagree — report
   the spread, never a single score as proof. A detector pass never overrides
   the human read: a draft can pass detectors and still read as AI, and the
   human read wins.
5. **Rules defence.** When a rule is flagged, the audit says which rule, why
   it fired, and what change clears it — or defends the exception with a
   reason. A flagged rule is never silently dropped.

## Rewrite rules
- Rewrite in a plain human voice: short sentences, concrete nouns, one idea
  per line, the user's actual words where they exist.
- Keep the user's facts; cut the filler. If the draft is missing the specific
  fact it needs, ask for it instead of inventing it.
- **Audit verdict given, always:** pass/fail + what still fails. A silent
  rewrite is not an audit.
- The audit applies to posts, comments, replies, and profiles alike — and to
  any draft this skill produces before it is shown as final.
