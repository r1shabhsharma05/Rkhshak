# Content States — every component, every state

A component is not done until ALL its states are designed. A screen that only works when data is present is a poster, not a product.

## The 4 states (every component that loads data)
| State | What it is | Design rules |
|---|---|---|
| **Loading** | Data is being fetched. | Skeleton loaders that match the final layout (same sizes, same positions) — never a generic spinner in the middle of nowhere. No shimmer on headings. Show skeletons for at most the expected wait; if it takes longer, show progress + a cancel/retry. |
| **Empty** | No data yet (first use, no results, cleared list). | A real empty state, not a blank screen: one line saying what goes here + the one action that fills it (e.g. "No invoices yet — Create your first invoice"). Never a dead band. The empty state is a doorway, so it may carry the moment (see pass 8). |
| **Error** | Something failed. | Plain language, what happened + what to do next + retry. Never a stack trace, error code, or "Something went wrong" with no action. The error state keeps the layout (don't collapse the page). Errors are announced to screen readers. |
| **Success** | The action completed. | Confirm briefly and specifically ("Invoice sent to aisha@example.com", not "Success!"). Then show the result or the next step. Don't trap the user on a success screen with nowhere to go. |

## Form states (every input, all 8 states)
Default · hover · focus (visible `:focus-visible`) · active/pressed · disabled (clearly disabled, never just greyed text that looks enabled) · error (message + icon + red border, linked to the field) · valid (subtle, not a green check on every field) · loading (submitting — button shows progress, form can't double-submit).

## Other states to design
- **Disabled actions:** say why when the reason isn't obvious (a tooltip or a line of helper text, not a dead button).
- **Partial data:** a list with some items failed to load shows the loaded items + a retry for the failed ones, not a full-page error.
- **Offline:** if the app works offline, the offline state is designed (what works, what doesn't, what syncs later).
- **Zero results (search/filter):** "No results for 'X'" + how to fix it (clear filters, try another term) + a way back. Never an empty table.
- **Long content:** truncation with a clear "show more", never text clipped mid-word with no way to read it.

## Rules
- The concept must survive every state. Walk the direction through empty, loading, error, and success. A concept that only works when data is present is a poster, not a concept.
- Skeletons match the final layout. A skeleton that looks nothing like the loaded screen is a lie that flashes.
- Never use a loading spinner as the moment. Loading is chrome — keep it quiet.
