# UX Writing — microcopy patterns

Words are interface. The right words make the product feel designed; the wrong words make it feel generated. Every word on screen earns its place.

## Voice (from the direction)
- The product's character sets the voice. Calm + exact → short, plain, specific. Warm + human → friendly, but never cute at the user's expense. Technical → precise, no jargon the user doesn't know.
- **Plain beats charming.** A short line trying to sound charming reads as AI. Say the plain thing.
- **Specific beats generic.** "Invoice #1042 sent to aisha@example.com" beats "Success!" A real number, a real name, a real date.

## Patterns
| Situation | Do | Don't |
|---|---|---|
| Button label | A verb + what it does: "Send invoice", "Save changes", "Delete account". | "Submit", "OK", "Click here", "Continue" (continue to what?). |
| Error message | What happened + what to do: "Card declined — try another card." | "Something went wrong", "Error 500", a code with no explanation. |
| Empty state | What goes here + the one action: "No invoices yet — Create your first invoice." | A blank screen, "No data", a dead band. |
| Loading | What is happening (if it takes >1s): "Sending invoice…". | A spinner with no context, "Loading…" forever. |
| Success | Specifically what happened: "Invoice sent to aisha@example.com." | "Success!", "Done!", an exclamation mark. |
| Confirmation (destructive) | What will happen + the consequence: "Delete this invoice? This can't be undone." | "Are you sure?", a vague warning. |
| Helper text | Only when the user needs it: password rules, format hints. | Helper text under every input (if it's obvious, delete it). |
| Onboarding | One thing per step, in the user's words: "Add your first client to send an invoice." | Feature tours, "Welcome to Acme! 👋", hype. |

## Rules
- **No exclamation marks** in interface text. Never `!!`.
- **No greeting headlines** ("Welcome back, ...!"). The title names the context.
- **No hype words** (supercharge, seamless, unlock, magic, revolutionize, game-changing, AI-powered on everything).
- **No trailing periods** on labels and buttons. Only paragraphs of several sentences keep their periods.
- **A change says what it compares to:** `+12% vs last month`, `3 fewer vs last month`.
- **Headlines say what the product does for whom, in plain words** — so they could not fit another product. Use the facts already on the page; never invent new ones.
- **Mock content is specific.** Never Maya, Sarah, Alex, Acme, or John Doe. Use a real-sounding person and detail.
- **Fake proof gets deleted.** If a claim can't be checked, ask, then make it specific or cut it.
- **Read it aloud.** If it sounds like a robot wrote it, rewrite it. If a competitor could paste it unchanged, rewrite it with this product's nouns.
