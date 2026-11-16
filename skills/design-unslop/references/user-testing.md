# User Testing — test the design with real people

A design the designer likes is a guess. A design real users can use is a result. Test before shipping — with 5 people, not 50.

## The 5-second test (first impression)
Show the screen for 5 seconds, then hide it. Ask:
1. What does this product do?
2. Who is it for?
3. What would you do next?
If the answers are wrong or vague, the headline, the moment, or the primary action is unclear. Fix that first — it is the most important test there is.

## Task test (can they use it?)
Give 5 people a real task ("Send an invoice to Aisha", "Change your password", "Find last month's revenue"). Watch them do it. Don't help, don't explain.
- **Measure:** did they complete it? How long did it take? Where did they hesitate, tap the wrong thing, or ask for help?
- **3+ people failing the same step = a design bug**, not a user error. Fix the step.
- **Record what they said** (their words, not your interpretation). "I didn't know where to tap" is a finding. "The user was confused" is not.

## What to test (in order)
1. **The first screen** (hero/landing) — 5-second test. If this fails, nothing else matters.
2. **The primary task** — the one action the product exists for. If users can't do it, the product is broken.
3. **The confusing screen** — the one with the most support questions, the most drop-off, or the most tells.
4. **A new feature** — before it ships, with 3–5 people who have never seen it.

## How to run it (cheap, fast)
- **5 people is enough.** After 5, you hear the same problems repeat. More people finds the same issues, not new ones.
- **Use real tasks, real data.** A test with fake data ("John Doe", "$123") tells you nothing about the real product.
- **Remote is fine.** A screen share + "think aloud" ("say what you're thinking as you go") works. Record it if the user agrees.
- **No leading questions.** Ask "What would you do next?" — not "Would you tap the blue button?" Never explain the design before the test.

## After the test
- **List the findings** (one line each: what happened, where, how many people). Sort by severity: blocked a task (Critical) → slowed a task (High) → cosmetic (Medium).
- **Fix the Critical + High first.** Re-test only the fixed steps (not the whole product) with 2–3 new people.
- **File the findings** with the DESIGN-AUDIT.md. A test nobody records is a test that never happened.
- **When to re-test:** before every major release, after a redesign, and when a metric drops (conversion, completion, retention).
