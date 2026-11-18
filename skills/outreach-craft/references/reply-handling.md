# Reply handling — a reply jumps the queue

## The rule
A reply is the goal of the whole run. When one lands, it outranks the
next batch: **never let a reply sit while the next batch goes out.**
Check the inbox before every send batch. If a reply arrived since the
last check, handle it first.

## Respond fast
- **Same day, ideally within hours.** A cold lead goes cold again fast.
  If the owner must answer (a pricing question, a call booking), draft
  the reply and put it in front of him the same day — do not queue it
  behind new outreach.
- **Cancel all pending follow-ups for that contact immediately.** A reply
  cancels the sequence; a follow-up sent after a reply is the fastest way
  to burn the relationship. Update the log row to `replied` the same day.

## Answer the actual question
- Read the reply twice before drafting. Answer what they asked — not the
  pitch you planned to send.
- If they ask about price, scope, timeline, or proof: answer with true,
  checkable facts only. No invented numbers, no invented customers, no
  "we usually" without a real basis. If the answer is unknown, say so and
  offer to find out — never fill the gap with a guess.
- If they ask for a demo, a call, or a link: send the real thing, not a
  promise of one. If no demo exists for this lead, say so honestly and
  offer the call instead.

## Move to a call or demo
- Every reply draft ends with one concrete next step: a call time, a
  demo link, or a yes/no question that moves the conversation forward.
  A reply that ends with "let me know what you think" is a stalled reply.
- Offer two specific times, not "sometime next week". Confirm the
  timezone explicitly — a missed call over a timezone mix-up is a lost lead.
- After the call/demo, log the outcome the same day (see
  `whatsapp-and-calls.md` outcomes) and update the roll-up.

## The replies you will actually get
- **Interested / yes:** move to call/demo immediately (above).
- **Not interested / no:** log `closed`, thank them in one line if a
  reply is warranted, never argue, never follow up again. A clean "no"
  is a good outcome — it closes the loop.
- **Gatekeeper / wrong person:** ask once for the right person or the
  right route. If they give one, log it and restart at verification
  (see `deliverability.md`) — a forwarded address is still a guess until
  verified. If they do not, log `closed`.
- **Question / objection:** answer the question, then ask the call
  question once. One objection handled well beats three follow-ups.
- **Out of office / auto-reply:** not a reply. Note the return date in
  the log and schedule follow-up 1 after it, not before.
- **Unsubscribe / stop:** stop immediately, log `closed`, never contact
  that address or number again on any channel.

## What a reply does to the triggers
- **One reply does not reset the 30-send trigger for the rest of the
  list.** The trigger measures the template's performance across the
  stream; a single reply is good news, not a new baseline. Note it in
  the roll-up, keep counting.
- **A reply rate above zero changes the diagnosis.** If replies start
  arriving, the diagnosis (see `diagnose-zero-replies.md`) shifts from
  "why zero" to "what is working" — log which version and which
  observation earned the reply, and protect that variable in the next
  rewrite.
