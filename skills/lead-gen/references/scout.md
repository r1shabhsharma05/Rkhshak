# Social-platform leads — scrape, enrich, score, export

Distilled from `scout` v1.3.1 (MIT, kiryano/Scout — interactive Python CLI
over 8 platforms with enrichment, scoring, CSV export). Own words; install
paths and local configuration are not carried over.

## Platforms (auth needs differ — check before promising)
| Platform | Auth | Notes |
|---|---|---|
| Instagram | None | May need retries; region/IP dependent |
| TikTok | None | May serve CAPTCHAs |
| LinkedIn | Session cookie, supplied by the user | Cookie expires; never paste it in chat, never use anyone else's |
| GitHub | None | Rate-limited unauthenticated |
| YouTube | None | Channel name, description, subs, email, links |
| Twitch | None | Falls back to direct connection if proxy fails |
| Pinterest | None | Profile, bio, followers, pins, website |
| Linktree | None | Link-in-bio platforms (Linktree, Stan, Bio.link) |

## Enrichment (in order)
1. Email/phone from bio text.
2. Website + /contact + /about deep scrape.
3. Company detected from headline; domain via DNS MX lookup.
4. Email pattern detection, candidate generation (first.last@, first@, …).
5. SMTP verification of each candidate (RCPT TO check — sends no mail).
6. Confidence score 0–100%.
- Optional paid lookup service for extra coverage where the user supplies a
  key through the secure flow. Free proxies are unreliable; say so before
  relying on one.

## Workflow
1. Ask the user for the essentials only: platform, who to find (usernames,
   niche, or a username list file), and whether to enrich.
2. Small validation first: one public profile before any bulk run.
3. Run the CLI; for bulk, use a username list file.
4. Present results as a lead list: name, platform, profile URL, email (with
   verification confidence), phone, website, followers, score.
5. Offer to save/filter/export CSV.

## Rules
- **Lead list, not verified truth.** An email/phone from a bio or guessed by
  pattern is not proof it is current or correct. Verify before calling or
  emailing; SMTP-verified still means "mail server accepts it", not "the
  person reads it".
- **Never auto-send, auto-contact, or auto-post.** Scout produces lead lists
  and drafts only.
- **Call-first** where a phone route exists; never lead with bulk cold
  SMS/WhatsApp.
- **Respect rate limits and CAPTCHAs.** If a platform blocks, report it and
  stop — do not hammer retries or rotate free proxies to evade a block.
- **Cookies and keys** come from the user through the secure entry flow,
  never in chat, never committed anywhere.
