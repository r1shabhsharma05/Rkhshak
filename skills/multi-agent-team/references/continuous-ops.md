# Continuous Ops — "continuously working", stated honestly

The team does not run 24/7 unsupervised. "Continuously working" means
three concrete things: scheduled runs, a shared queue, and a report
after every run. Anything beyond that is a claim, not a fact.

## Scheduled runs
Daily and recurring jobs run on the owner's approved schedule — one
schedule per job, approved by the owner, recorded on the board:

| Job | Role | Schedule (example — owner's approval decides) |
|---|---|---|
| Job applications | Job Applier | Daily, on the approved time |
| Lead sweep | Agency Owner | On the approved days |
| Social drafts | Editor | On the approved days |
| Research watch | Researcher | When the owner asks, or on the approved cadence |

- A schedule is approved by the owner for that job. A yes to one run
  is one run; making it recur needs its own approval naming the
  schedule.
- Each scheduled run is one execution of the loop: brief → do →
  report → verify → Master reports to the owner. A scheduled run with
  no report did not happen, as far as the owner is concerned.
- If a scheduled run fails, is blocked, or finds nothing, the report
  says so. "Nothing found today" is a result, not a failure — but
  silence is never a result.

## The shared queue
Work that arrives between runs waits in one queue on the board:

```
QUEUE:
  1. [Job Applier] Apply to <role> at <company> — added <date> — status: waiting
  2. [Editor] Draft carousel on <topic> — added <date> — status: waiting
```
- One queue, visible to the whole team. A job is claimed by its role,
  worked, and marked done with its evidence — or returned to the queue
  with the blocker named.
- The queue is the only place new work enters. Work that arrives by
  any other route (a DM, a side note) is posted to the queue by the
  Master before anyone starts it.
- The Master reviews the queue on every run: stale items (older than
  the owner would still want) are flagged to the owner, not silently
  worked or silently dropped.

## Per-run report (the Master sends the owner)
```
RUN: <job> — <date/time>
DID: <what was done, concrete>
FOUND: <results — applications, leads, drafts, with counts>
EVIDENCE: <confirmations, links, files — or "none, blocked by X">
OPEN: <what is still waiting, and what needs the owner>
NEXT: <the next scheduled run>
```
- Outcome + evidence, every run. No run is reported as complete
  without its confirmation. No "probably submitted", no "should be
  live".
- Hard stops still bind every scheduled run: no auto-posting, no
  sending without the owner's word per channel, no submission claimed
  without confirmation, no deploy without the owner's explicit word.

## Honest limits
- **Agents do not run unsupervised forever.** They run on demand and
  on schedule, and each run ends with a report. A run that nobody
  watched and nobody reported is not a run.
- **A schedule is not a promise of results.** Daily applications do
  not promise daily offers; lead sweeps do not promise daily replies.
  The report states what happened, not what was hoped.
- **Costs and limits are real.** Every run spends time, tokens, and
  rate limits. If a job's cost or volume grows past what the owner
  approved, the Master stops and asks before continuing.
- **The owner can pause or kill any job at any time.** A stop is
  acknowledged at once, dispatch halts, and the Master reports the
  verified resume point. A job that cannot be stopped is a job that
  should never have started.
