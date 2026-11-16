# Prose Tells — the 26 AI writing patterns (from blader/humanizer)

Code has prose in it: comments, docs, commit messages, READMEs, error messages, UI copy. The same AI tells that mark prose also mark code. This file is a summary of the 26 patterns from **blader/humanizer** (MIT, https://github.com/blader/humanizer, v4.0.0), built on Wikipedia's "Signs of AI writing". Use it on every piece of prose in and around the code — not just the code itself.

## How to work
1. **Mark the tells.** Read the whole text once, mark every pattern, strongest first (§1–§5 justify an edit on one sighting; a pattern marked *weak alone* needs company from other tells in the same passage).
2. **Draft the rewrite.** Keep every supported claim. Shorten dull parts, merge or split sentences. Where the text is generic, add a specific detail you know to be true. If a detail is missing, ask for it or write a simpler sentence.
3. **Check the draft.** Did the rewrite drop or change any fact, name, number, date, or claim? Read it aloud — what still sounds AI-generated? Search again for the tells that survive rewrites most often: §1, §2, §6, §8, §19.
4. **Write the final version.** State each point naturally, don't patch flagged phrases one at a time. Vary sentence length.

## A. Staging instead of stating (strongest — act on one sighting)
| # | Pattern | Before | Fix |
|---|---|---|---|
| 1 | **Not X but Y** | "It's not just a feature, it's a shift." | State the point directly. Keep a contrast only when the negative half corrects a belief the reader actually holds. |
| 2 | **One-line closers** | "That is the real win." after every section; "Let that sink in." | Cut the closer that repeats or explains the example. Keep it only when it adds a fact the example doesn't show. |
| 3 | **Sayings that sound deep** | "At its core, what really matters is..." | Replace the saying with the specific claim. |
| 4 | **Staged run-up** | "Let's dive in", "Honestly?", "Here's the thing" | Remove the run-up and state the point. |
| 5 | **Arguing with no one** | "This isn't mainly about...", "A tempting approach would be..." | Remove the unraised objection. Keep an objection the text actually answers. |

## B. Rhythm by rule
| # | Pattern | Before | Fix |
|---|---|---|---|
| 6 | **Forced triads** | "innovation, inspiration, and insights" | Use the number of items the meaning needs. |
| 7 | **Repeated sentence openings** | "She noted... She noted... She filed..." | Merge the sentences or change the subject. |
| 8 | **Dashes everywhere** (*weak alone*) | "institutions—not the people—yet this continues—" | Use periods, commas, colons, or parentheses. (Leave dashes inside code, commands, paths, URLs alone.) |
| 9 | **Stacked qualifiers** (*weak alone*) | "could potentially possibly be argued" | Keep only qualifiers the source supports. |
| 10 | **Hyphenated pairs everywhere** (*weak alone*) | "the report is high-quality" (after the noun) | Keep the hyphen before the noun; drop it after ("the report is high quality"). |
| 11 | **Passive voice / missing subjects** (*weak alone*) | "No configuration file needed." | Name the actor when it helps: "You don't need a configuration file." |

## C. Inflation and borrowed authority
| # | Pattern | Before | Fix |
|---|---|---|---|
| 12 | **Overused AI words** | delve, crucial, pivotal, robust, showcase, testament, landscape, intricate, meticulous, vibrant | Use plain words. |
| 13 | **Inflated significance** | "marking a pivotal moment", "the future looks bright" | Keep the fact, drop the significance. End on the last concrete fact. |
| 14 | **Vague connection** | "associated with the leadership of..." | Name the relationship. If you don't know it, keep the vague wording. |
| 15 | **Shallow -ing phrases** | "symbolizing...", "reflecting...", "showcasing..." | Keep only what the source supports. |
| 16 | **Sales language** | "nestled in the breathtaking region", "must-visit" | State what the thing is. |
| 17 | **Borrowed authority** | "Experts believe...", "cited in NYT, BBC, FT" | Name a real source and what it said, or remove the claim/list. |
| 18 | **Avoiding is/are/has** | "serves as", "features", "boasts" | Use "is", "has". |

## D. Formatting by rule
| # | Pattern | Before | Fix |
|---|---|---|---|
| 19 | **Bold as decoration** | "**OKRs**, **KPIs**"; "**Performance:** ..." | Remove the bold; turn a labeled list into prose. |
| 20 | **Decorative headings** | "Strategic Negotiations And Partnerships", "🚀 Launch Phase:" | Sentence case; remove emojis and arrows; name what the section holds. |
| 21 | **Curly quotes** (*weak alone*) | said “the project” | Use straight quotes: said "the project". |

## E. Leftovers from the chat and the draft
| # | Pattern | Before | Fix |
|---|---|---|---|
| 22 | **Chatbot residue** | "Great question!", "I hope this helps!", "Of course!" | Remove the wrapper, keep the content. The most certain tell in the list. |
| 23 | **Knowledge-limit disclaimers / guesses** | "While details are limited...", "it appears...", "likely grew up..." | State what the source shows, or remove the sentence. |
| 24 | **Heading repeated in first sentence** | "## Performance" + "Speed matters." | Let the heading do the work. |
| 25 | **Writing about the document** | "This function was added to replace...", "The table below compares..." | Describe the subject. Mention a previous version only in changelogs/release notes. |

## F. Writing for the wrong reader
| # | Pattern | Before | Fix |
|---|---|---|---|
| 26 | **Re-explaining what the reader knows** | A reply that walks the diagnosis and proves the plan before the decision. | Lead with the decision. Keep only the reasoning that would change whether the reader agrees. |

## Voice matching
If the user gives a writing sample, read it first and match its sentence length, word choice, punctuation, openings, and transitions. The sample overrides the patterns — including §8: if the sample uses dashes, keep them at about the same rate. Without a sample, personal writing keeps opinions, uncertainty, and humor; technical/reference prose stays neutral and plain.

## When NOT to act
- Leave a watched phrase alone inside a quotation, a title, a proper name, or a passage discussing the phrase itself.
- Keep the details that carry the writer's voice: specific unusual details, mixed feelings, dated references, first-person choices, genuine asides.
- Text written before 30 Nov 2022 is not AI-written.
- One tell alone is weak evidence. Several tells together are the safeguard.

## What this is NOT
This skill edits for human readers. **It does not try to get past AI detectors, and detectors still flag most of its output.** Never claim a rewrite will pass a detector. Never use it to deceive — if asked whether AI wrote the text, answer honestly.

## Source
Patterns from [blader/humanizer](https://github.com/blader/humanizer) (MIT, v4.0.0, 69k+ stars), built on Wikipedia's ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) (WikiProject AI Cleanup).
