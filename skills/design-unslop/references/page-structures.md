# Page Structures — anatomy, shapes, scroll, brand truth

Distilled from Hallmark v2 (method in our own words; the shape catalogue and choreography rules are summarised, not copied). Use when a new page needs a shape, a scroll story, or a real brand's truth.

## Anatomy: build from the job
Name what a visitor comes to do, then build the page from that category's anatomy — where real sites in the category put the action, the sections they are built around, and how they end. Never from a default run of figures, steps, and an email band.
| Job | Page is built around |
|---|---|
| Subscribe (newsletter, waitlist, podcast) | The promise + the first issue, the ask |
| Book (restaurant, class, clinic, studio) | Availability, the room/table, the booking |
| Visit (shop, gallery, venue, place) | The place, hours, how to get there |
| Attend (event, festival, race, conference) | The line-up, the date/place, tickets |
| Buy (physical product, small shop) | The product, its variations, the price |
| Try (app, game, desktop tool) | The product doing its one job, live |
| Sign up (software, API, developer tool) | The setup, the first result, the docs |
| Hire (studio, freelancer, architect) | The work, the process, the contact |
| Join (club, community, membership) | The people, the ritual, the door |

## The 21 macrostructures (pick one per page, from the material)
A page with pictures leads with them; a page about words carries type and facts. Read only the shape you land on; never load the whole catalogue. Nav and footer are part of the shape, settled with the hero.
1. **Bento Grid** — modular blocks of varying sizes; rhythm from size variation, not card uniformity.
2. **Long Document** — reads like a memo or letter; continuous prose with inline section heads.
3. **Marquee Hero** — the hero is the page above the fold; below it the page becomes something else.
4. **Stat-Led** — the hero is a figure the user gave, with the line that says what it means.
5. **Workbench** — real product captures are the primary content; a guided tour of the app in use.
6. **Conversational FAQ** — bold questions, prompt answers; reads like an honest interview.
7. **Manifesto** — polemical large type; tells the reader what to believe before what to buy.
8. **Photographic** — one huge image dominates each fold; text is small annotation.
9. **Quote-Led** — the hero is a quote the user supplied, with its attribution.
10. **Specimen** — large serif display, asymmetric spans; only for prompts about type, publishing, or writing.
11. **Catalogue** — uniform grid of variations of the same thing; a visual index of inventory.
12. **Letter** — first-person, written, intimate; opens with a greeting.
13. **Index-First** — the page is a list of links; navigation as design.
14. **Narrative Workflow** — numbered stages tell how the user uses the product over time.
15. **Split Studio** — diptych; text on one side, proof on the other; rows vary by weight.
16. **Feature Stack** — sticky left pane holding the heading, scroll-synced right pane cycling captures.
17. **Type Specimen** — the typeface is the design; foundry pages and design systems.
18. **Project Grid** — filterable cards of projects; the work is the product.
19. **Map / Diagram** — one large spatial diagram organises the page.
20. **Ecosystem Index** — multiple discovery surfaces; the value is browsing, not declaration.
21. **Component Playground** — interactive code-and-preview blocks are the primary content.

**SaaS section deck: deal it, do not sequence it.** When the prompt names no shape, deal a trio of sections and let the material pick — never default to the same section order twice. **Mirror test:** would a neighbouring prompt in the same category get this exact combination? If yes, change one decision and say which.

## Custom direction (no theme)
When the user asks for custom / bespoke / "a world of its own", the design is yours: it replaces the dealt theme, the shapes, and the genre files. The Floor, the gates, and the sweep still bind. Silence never takes this route.

## Scroll choreography: the one earned pattern
Default is still none — the reveal-once is the page norm. A scroll-linked pattern is used once, on structure, when the content has a sequence worth pinning or scrubbing.
- **Budget:** one pattern per page. Never on body text — targets are structural (a pinned section, one display element, a 2px spine, figures). Prose never moves under the reader.
- **Static end-state mandatory.** Base CSS shows the finished layout. The choreography lives entirely inside `@supports (animation-timeline: view())` and `@media (prefers-reduced-motion: no-preference) and (min-width: 40rem)`; reduced motion, small screens, and browsers without support get the complete page.
- **Linear is correct here:** scrubbing maps scroll distance to progress one to one; an easing curve detaches the page from the thumb. Declare `animation-timeline` and `animation-range` after the `animation` shorthand (the shorthand resets them).
- **The four patterns:** (1) **Pinned chapter** — steps reveal while the section is pinned (tall track, sticky pane, steps consume the timeline in slices). (2) **Scrub-linked headline** — one display element, clip wipe. (3) **Progress spine** — `scroll(root)` scaling a 2px rule. (4) **Sticky diptych** — a two-pane pin. Pick one; a second pattern family on the same page is a failure.

## Brand truth: never theme a real brand from memory
When the prompt names a real brand, fetch its brand spec (colours, typefaces, logo rules, voice) from the brand's own published material and record it with the fetch date. Theme from that spec, never from memory. Cache it and note staleness; if fetching is impossible, say so and build from the project's own assets instead of guessing the brand. This protocol never invents brand values.

## Texture (budgeted vocabulary)
Texture is a budgeted device, not a default: grain (paper), halftone (dot field), misregistration (chromatic echo), scanline (CRT), deckle (paper edge). One texture per page at most, only when the theme names it, and only where the subject earns it (print, archive, broadcast). Keep it out of text and out of reduced-motion variants.

## Page invariants
One primary button style, one container width, one column gap below the hero, one radius per nesting level, never more centred heading groups than left-aligned ones. Hero: a headline of seven words or fewer, one sentence of twelve words or fewer, one or two actions. Six to nine sections, hero and footer included. 450 visible words at most. The container is capped and centred: at 1920 the gutters grow, the measure and the grids do not.
