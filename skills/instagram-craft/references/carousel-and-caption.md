# Carousel and caption

## Carousel
Carousels are the highest-dwell format on the grid: a swipe is an interaction and a scroll is not. They also get a second chance — Instagram can show a carousel again starting from a later slide, so slide two has to stand on its own.

**When to use it instead of a Reel**: the idea has sequence and needs to be re-read — steps, a framework with parts, a before and after, a list worth screenshotting. Use a Reel when the idea has motion, a face, or a payoff that has to be seen happening. If the idea is one claim, it is neither — hand it to the Reel workflow.

**Structure** — 6 to 10 slides (cap is 20; under 5 the swipe never starts):
```
1       COVER   the hook. 6 words or fewer, legible at grid thumbnail size. One line of promise under it.
2       STAKE   why this matters, in one sentence. Also a second cover — it cannot be setup.
3–N    ONE IDEA PER SLIDE. Headline 3–7 words, at most 25 words under it. A slide that needs a paragraph is two slides.
N+1     RECAP   the whole thing as a list. The screenshot slide.
LAST    CTA     one action. Save, comment a keyword, or follow. One.
```

**Slide copy rules**: the cover is 80% of the result — six words, big. Design for the grid crop: build at 1080×1350 and keep cover text well inside the middle, clear of the outer 120 pixels on every side. Number the slides (3/8) — completion goes up when people can see the end. No slide is a paragraph. The recap slide is the one people screenshot and send; make it standalone and readable with no context. Handle on every slide, small, bottom corner — screenshots travel without you. Alt text on the cover at minimum.

**Building the files**: 1080×1350 (4:5), JPEG or PNG, up to 20 items. Build as HTML (one `<section>` per slide, `width:1080px; height:1350px`, single accent colour, type no smaller than 32px — this is read on a phone at a third of its real size), then print each slide. If the user has a brand system, use it; do not invent a palette.

**Output**: slide-by-slide copy first (a numbered list the user can read in ten seconds and edit before anything is rendered), then the caption — Job B, below. Run both through the humaniser. Build the files only after the user approves the copy. Nothing is uploaded. The user posts it.

## Caption
**First, decide which job this caption has.** Skipping this decision ruins captions.
- **Job A: the video already hooked them.** A Reel carries its own hook in the first two seconds. The caption is not a second hook — competing with the video loses both. Its job is the ask, the context that makes the ask make sense, and the words people search.
- **Job B: the caption is the content.** A photo, a single image, a carousel cover that opens a loop. Line one is the hook and works exactly like a Reel hook: concrete, short, cut off at a cliff rather than mid-clause.

**The shape**:
```
Line 1     125 visible characters. Job A: the ask, plainly. Job B: the hook.
           Never a greeting, never a hashtag, never an emoji as the first character.
Body       short paragraphs, one line of white space between each. Two to six of them.
           This is where the search terms live.
The ask    one. Comment a keyword, save it, or DM. One.
Hashtags   up to five, on their own line at the bottom, or none.
```
Limit is 2,200 characters and almost nothing needs 2,200. A caption that earns the tap and delivers 600 characters beats one that delivers 1,800.

**Hashtags, honestly**: hashtags are not a reach lever any more — Instagram capped hashtags at five per post (December 2025) and has said they are a label, not a distribution lever. So: up to five, specific, as topic labels. `#viral`, `#fyp`, `#explorepage`, `#foryou` describe nothing. Cut them. A saved block of twenty is dead weight and the linter will fail it.

**Search terms matter more than hashtags**: Instagram search reads the caption text. The phrase the user wants to be found for goes in the caption as a phrase a human would type, in a sentence that reads normally. Ask for two or three terms, then pass them to the linter.

**Rules**: no link in the caption (captions are not clickable — bio or DM); one ask (two asks is the same as none); the keyword ask needs a keyword people can type — one word, no spaces, no emoji, said out loud in the video too (`Comment CONTRACT` works; `Comment "the contract guide"` does not); write the first comment separately if there is a link; emoji as punctuation, not decoration (the linter flags more than 4 per 100 characters); alt text is worth 20 seconds on carousels and photos.

**The loop**:
```bash
python3 scripts/caption.py draft.txt --keywords "client proposals,agency pricing"
```
1. Decide Job A or Job B and say which. 2. Draft. 3. Humanise. 4. Run `caption.py` with the user's search terms; fix every FAIL; decide on every WARN out loud. 5. Print the copy-ready block, then the receipt (job, visible characters used of 125, ask, hashtags, search-term placement, linter verdict). Nothing is posted. The user pastes it.
