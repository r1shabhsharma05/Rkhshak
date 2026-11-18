---
name: linkedin-craft
description: "Plan, draft, audit, and humanise LinkedIn posts, comments, replies, and profiles — DRAFT ONLY. Use when the user wants to write a LinkedIn post, draft a comment or reply, audit a draft, extract a hook formula, plan a week of content, or rewrite a profile. The owner posts himself; this skill never posts, comments, reacts, or schedules anything live."
---

# LinkedIn Craft — draft only, the owner posts

## Purpose
LinkedIn rewards specific, human, evidenced writing — and punishes generic
AI-sounding posts, invented traction, and copy-pasted virality. This skill
plans, drafts, audits, and humanises LinkedIn content from the user's real
experience, and stops at the draft. The owner posts himself.

Use it when the user wants to write a post, draft a comment or reply on a
post, audit a draft, remove AI tells, extract a hook formula from a viral
post, plan a week of content, track a thread, analyse engagers, rewrite a
profile, run employee advocacy, repurpose content from another platform, or
work out what they actually have to say. For job applications, use
job-search; for lead outreach, use lead-gen.

## DRAFT-ONLY RULE (stated first, applies to every workflow below)
- **This skill never posts, comments, reacts, or schedules anything live.**
  Every approved draft is returned as a copy-paste block with the target URL.
  The owner posts it himself.
- If the user asks to publish and no publishing backend is connected, lead
  with the wall **once**, first line, before the draft: one sentence on what
  did not happen and what would change it. Then the draft. Do not raise it at
  all when the user only asked to draft, plan, rewrite, or audit — nothing is
  missing in that case. Once per conversation, not per draft. **Never after a
  decline** — "not now", "I'll paste it myself", or silence on the offer is
  final for the session. Do not re-ask on the next draft.
- A publishing backend (publishing API or a custom poster the owner built) is
  the owner's setup, his keys, his yes. Keys live in the owner's environment,
  never in chat, never in a file the skill writes.

## Core pattern (every content action)
1. **Parse the input.** The user provides a LinkedIn URL (post or comment)
   or pastes the text. Without a read layer, pasted text is the source — say
   so; never claim to have read a live thread that was not read.
2. **Draft the content.** From the user's real experience and the story bank
   (see below), using the hook formulas and voice rules. No invented numbers,
   companies, or outcomes.
3. **Wait for approval.** The user replies with approval or edits. Only the
   owner posts — there is no step 4 that publishes.

## Voice rules (baked into every draft)
- **Start from the story bank, not from nothing.** If the user has never
  posted, interview them first and keep the answers in a story bank — a
  career is enough to start. Every writing workflow reads the story bank.
  If a draft has nothing concrete to use, say so and ask for the real
  material instead of inventing it.
- **Extract formulas, never copy posts.** A hook formula is a structure
  (rejection-count open + turn + lesson); the viral post's text stays the
  viral post's text. A draft built from a formula uses the user's own facts.
- **Remove AI tells before delivery.** Emoji stacks, "excited to share",
  "in today's fast-paced world", "leveraging cutting-edge" — flagged and
  rewritten in a plain human voice with specifics. Audit every draft
  pre-publish; see `references/humanizer-audit.md`.
- **Founder content compounds trust with a narrow audience** instead of
  chasing broad reach. Founder angles and structural formulas are in
  `references/profile-and-planning.md`.

## References
| File | What it covers |
|---|---|
| `references/post-writing.md` | Post writing — hook formulas, post structure, hook extraction |
| `references/comments-replies.md` | Comments and replies — drafting, thread sweeps, thread monitoring, engager analytics |
| `references/profile-and-planning.md` | Profile optimiser + content planner — pillars, founder angles, weekly plans |
| `references/repurpose-advocacy.md` | Repurposing + advocacy + interviewer — cross-platform adaptation, team advocacy, story bank |
| `references/humanizer-audit.md` | Humanizer audit — AI-tell removal, emoji density, detector audit, pre-publish review |

## Provenance
Distilled in our own words from `linkedin-skills` (MIT bundle of 12 focused
skills; 81+ reference files distilled, NOT copied — no source file reproduced).
Third-party services named in the source (a publishing API, a read-side
scraping platform) are described as the owner's optional setup with their own
terms; no keys, tokens, or accounts are carried over. No project names,
personal data, or credentials carried over.

## Report format
Draft (copy-paste block + target URL) · what was not done (not posted — owner posts) · audit verdict (pass/fail + what still fails, if audited) · source of every fact in the draft (story bank / user-stated / `[N]` placeholder) · next step (one line).
