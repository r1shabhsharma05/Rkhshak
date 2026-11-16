# README + Docs Voice — write docs that sound like a person

A README is the first thing a stranger reads about a project. If it sounds like a template, the project sounds like a template. Write like a person explaining it to a colleague.

## Rules
- **What, why, how — in that order.** What it is (one sentence), why it exists (one or two sentences, the real reason), how to use it (commands that work, copied from a real run). Anything else goes after.
- **Concrete examples first.** Show a real command and its real output before explaining the options. A reader who sees it work trusts the rest of the doc.
- **No marketing fluff.** "Seamless", "cutting-edge", "revolutionary", "blazingly fast", "delightful" — delete them all. If the thing is fast, say how fast (a number). If it's simple, show the three commands that prove it.
- **Real commands that work.** Every command in the doc was run, in order, from a clean checkout. A command that fails on first use destroys trust in the whole doc.
- **Honest limitations.** Say what it doesn't do, what it needs, and where it breaks. "Requires Node 20+", "doesn't work on Windows yet", "no offline mode" — honesty is a feature.
- **Short sentences, short sections.** A section longer than a screen gets split or cut. A sentence longer than two lines gets rewritten.
- **Write like you talk (a little).** Contractions are fine. "You" is fine. A doc that sounds like a person is easier to follow than one that sounds like a manual.
- **No stock AI words.** "Delve", "leverage", "furthermore", "moreover", "in today's fast-paced world", "it's important to note that" — these are tells (see `references/prose-tells.md`). Cut them.
- **Structure a stranger can scan.** Headings that say what the section is, code blocks for commands, tables for options. A reader should find what they need in 10 seconds.

## The test
Give the README to someone who has never seen the project. Can they install it and run it, using only the README, in under 10 minutes? If not, the README failed — rewrite it, don't add a "troubleshooting" section that apologises for it.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | What / why / how in that order | A README that starts with badges and a feature list |
| 2 | Real example before explanation | Options documented, no working example shown |
| 3 | No marketing fluff words | "Seamless", "cutting-edge", "revolutionary" present |
| 4 | Every command verified from a clean checkout | A command that fails on first run |
| 5 | Limitations stated honestly | A known limitation hidden or unmentioned |
| 6 | No stock AI words | "Delve", "leverage", "furthermore" present |
| 7 | Stranger test: install + run in under 10 minutes from the README alone | They get stuck |
