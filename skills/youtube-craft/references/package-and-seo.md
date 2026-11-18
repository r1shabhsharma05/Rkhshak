# Package and SEO

## The title and the thumbnail are ONE unit
Writing them separately is why most packaging fails: the thumbnail repeats the title, and half the click surface says the same thing twice.

```bash
python3 scripts/title.py --title "..." --thumb "AI RAN IT"
python3 scripts/title.py titles.txt            # one per line, ranked
```

## Before you write
1. Read the voice profile. If it does not exist, build it from three of the user's own videos.
2. Never invent a number, a result, or a source. If a figure would strengthen the title and you do not have one, ask for it or write the title without it.

## Rules the tool enforces, and why
- **60 characters** is where desktop search truncates; **40** is a mobile home feed. Both are reported because they fail differently: a desktop cut loses the tail, a mobile cut can lose the subject.
- **The thumbnail must not repeat the title.** Different words, same promise.
- **Three words maximum on the thumbnail.** At feed size a fourth word is a grey smear.
- **A number, a name, or a date** beats every adjective available to you.
- **Two all-caps words is the ceiling** before a title reads as spam.

## Write ten, keep two
Generate ten titles, run them all through `title.py`, show the user the top three with their scores and the specific issue on each. For the winner, write the thumbnail brief: the expression, the framing, the three words, and what the background has to do to hold contrast at feed size.

## Description, tags, and the query test (YouTube search text)
Search is a smaller lever than packaging and a bigger one than people think for evergreen videos. For a video aimed at the subscriber feed, say so and spend the effort on packaging instead.

**The description**:
- The first two lines are the only ones anyone reads. They show above "…more" and they are the search snippet. Say what the video gives them, in the words they would have typed.
- Then the link or the resource, if there is one, so it is above the fold.
- Then chapters (the chapters workflow writes them).
- Then the long version: what is covered, who it is for, what it assumes.

**Tags, honestly**: tags are a weak signal and YouTube has said so. Use them for disambiguation — spellings, the tool names, the abbreviations people actually type — and stop. Fifteen is plenty. A wall of tags is not a strategy, and stuffing unrelated ones is against the terms.

**The query test**: before handing anything over, write the three search queries this video should win, and check the title and first two description lines contain the words in those queries. If they do not, the problem is the title, not the description.

For website SEO — pages, schema, sitemaps, rankings — use the `seo` skill. This reference owns only the search-facing text of a video.

## The gate
Nothing here publishes. Every output ends in a block the user copies, and the last line of every run is the question: **ship it, or change it?**
