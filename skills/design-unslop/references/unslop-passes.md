# Unslop Passes — the 9 passes, in order

Finish each pass across the whole screen before starting the next. Order matters: rhythm changes how everything else reads, copy length decides type size and layout, visuals and motion come last so they fit a screen that already works without them.

## Subtract first (before the passes)
Walk every icon, line, badge, caption, container, and word and ask: **what breaks if this is gone?** "Nothing" means delete. "It adds interest" and "it fills space" don't count. Walk twice. The one signature from the direction is exempt, and only that one. If an element carries information people need (a password's rules, a price), move it, shrink it, or make it the moment; don't lose it.

Cuts generated screens need most:
- **Dividers.** Delete every divider that spacing can replace; proximity already groups things. Lines in a ledger or table that help the eye track across a row can stay.
- **Subtitles under titles.** Delete unless they say something the title can't.
- **Nesting.** A container inside a container inside a card is a tell. If a map, image, or chart is the content, run it to the edges of its parent.
- **Two mechanisms for one job.** Keep the better one. The job still gets done.
- **Bolted-on controls.** A button floating beside a field belongs inside the field.
- **Chrome the moment doesn't need,** like a Share button on something with nothing to share yet.

## 1. Spacing
- Everything on a 4px grid. Replace one-offs like `mt-[13px]`.
- Same thing, same size: one row height, one gap, one card padding per set.
- Gaps inside a group are smaller than gaps between groups, so grouping needs no lines.
- Icons sit in one column, labels start on one line, numbers right-align. Nothing nudged off its line.
- Padding follows density: compact panels/sidebars ~16, cards 20–24, page edges 24–32. Navigation is the densest part (rows 32–36, 2–4 between).

## 2. Color
- One neutral ramp tinted toward the world, with three text roles (primary, secondary, muted). Five lavenders means nobody chose.
- One accent in the chrome, covering a few percent of the screen. Derive the hue from the world — unchosen purple is the loudest tell.
- Working screens (apps, dashboards) keep neutral surfaces; color lives in the content. Landing pages can tint surfaces further toward the world.
- Delete gradient text, colored glows, colored shadows, neon borders, blobs behind content.
- Text keeps 4.5:1 contrast, including over backgrounds. Accent with text on it reaches 4.5:1.
- On dark themes, depth comes from surface steps and hairlines, not shadows. Shadows are neutral, soft, and small.
- A gradient is allowed only as a small tone shift inside one neutral (e.g. an active row going from #2b2b2b to #1f1f1f). Never from one hue to another. A gradient is slop as decoration and craft as material — what decides it is whether it has a reason, a chosen palette, and quiet UI on top.

## 3. Icons
- Emoji become line icons from one set, at one size and stroke (16–18px, 1.5 stroke), in a text role's color. Emoji can't take your palette.
- **Exception: third-party logos keep their real colors.** Google multicolor and Facebook blue are recognized before they're read. Grey logos make people read.
- ✨ doesn't mean AI. If AI matters, the copy says what it does.
- An icon's end state must read on its own at 20–24px. If it needs its animation to make sense, redraw it.
- Drop icons that add nothing (emoji in every card title, before every section label).

## 4. Copy
- Could a competitor paste this headline unchanged? Then rewrite it with this product's nouns.
- No exclamation marks, greeting headlines, hype words, or trailing periods on labels and buttons.
- A change says what it compares to: `+12% vs last month`.
- Read each line next to what's already on screen. If it repeats a number or word nearby, cut it.
- **Mock content is specific.** Never Maya, Sarah, Alex, Acme, or John Doe. Use a real-sounding person and detail.
- Fake proof gets deleted. If a claim can't be checked, ask, then make it specific or cut it. A real number is the strongest copy there is.

## 5. Type
- Choose type for the character. One interface family plus at most one partner, used for one distinctive decision. A display face appears once.
- Weights 400–500, 600 for rare emphasis. Hierarchy from size and color, never 800–900.
- Sentence case. Uppercase with wide tracking becomes sentence case, unless the real object you borrowed is uppercase (a stamped tag, a boarding pass).
- `tabular-nums` and one number format across the screen. Negative tracking only on display sizes.

## 6. Layout
- Everything stacked and centered, three equal cards, bento grids, and a picture panel beside a form column are all defaults. Size by content: give the important thing more room and let content break symmetry. To get out of the form-beside-picture default, let the form sit in the material rather than beside it.
- Check the largest viewport too. A dead band is empty space with no material and no job. Fill it with the world (a surface, real content) or compose the form into it; don't just scale the type up.
- One primary action and at most one secondary.
- Apps keep real app proportions. Heroes are composed as a whole first screen with no dead band.
- The smallest viewing size is a layout. For a video or thumbnail, and only then, keep 24–32px of air, let nothing hit the frame edge unless it's meant to bleed, and keep every word people need at 16px or larger at that size.

## 7. Details
- Inner radius = outer radius − padding, never below 4. Not everything is a pill, and `rounded-2xl` isn't an answer.
- Control shape comes from the character, not the token table. Exact and technical: 2–6px, thin fields. Soft and human: larger radii or full pills. Editorial: underlined fields, text buttons. Justify the shape from the character in one sentence.
- One depth cue per surface. Border + shadow + ring + gradient is a model hedging.
- No dotted lines or dotted dividers unless the object is really perforated.
- Stat cards are numbers: no sparklines or icons to fill them. One main chart, one accent per chart.
- Hover and focus exist and stay inside the palette.

## 8. The moment
Sketch one idea from each of these, in a sentence each:
1. **Behaviour:** something the interface does that only this product would do. It may look plain at rest.
2. **Real content:** the product's data, drawn with care, or its actual output.
3. **Proportion:** the important thing takes 70% of the screen and everything else gets out of the way.
4. **Type:** one size contrast, one huge number, or one line of copy set as the whole screen. It must carry meaning: the number is the answer, or the sentence changes as the state does. A big "Log in" fails, because the word isn't saying anything.
5. **A surface or object,** using the tree below.

Keep the one that passes both tests: **Is it an idea?** (take away the styling and describe it — "huge serif headline" isn't, "the invoice total is the page, and each paid line crosses itself off it" is) and **Is the rest frame good on its own?** (most people only see the first state, so an idea that only appears after typing needs a rest frame that's already composed and already from this product's world).

Then build its next state too. A concept you've only drawn isn't tested.

```
How long do people stay on this screen?
├── Minutes or daily (app, dashboard, settings, chat in use)
│   → neutral surface. The moment is content.
└── Seconds, as a doorway (login, empty state, confirmation, hero)
    → a field or object is allowed if it passes all five:
      1. Reason: someone who hasn't seen your concept can guess why it's here.
      2. Palette of at most three hues, taken from the world.
      3. Real structure: light, depth, focus. A two-stop wash is not a field.
      4. The UI on top stays quiet and legible.
      5. Stock check: at the viewing size, could this come from an illustration pack or a template gallery? Layered flat hills, gradient suns, and a dashed trail fail. If it does and two attempts don't fix it, go back to 1–4.
```

**Characters and illustration** must look drawn for this page: colors from the page's palette, features in its ink, one line weight, no solid black masses or glove hands. If it reads as a sticker or emoji, redraw or remove it.

## 9. Motion
- Delete motion by default: looping pulses on things that aren't live, shimmer on headings, breathing glows, parallax, `transition-all`, `hover:scale` on cards, every section fading in on scroll.
- Keep motion that explains something.
- One smooth-scroll engine only (Lenis or Locomotive, never both). GSAP for choreographed sequences. CSS for simple hover, focus, and tap states. Reserve ScrollTrigger for justified scrubbed or pinned sequences.
- Bypass smooth scrolling and scrubbed timelines under `prefers-reduced-motion: reduce`. Render final states immediately instead of merely shortening animations.
- Pointer effects are additive. Support touch, keyboard, coarse pointers, window blur, and visibility changes without leaving the interface incomplete. Design a static first frame that remains complete when JavaScript, media playback, WebGL, or motion is unavailable.
