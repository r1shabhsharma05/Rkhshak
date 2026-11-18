# Observability — make production behaviour visible

Distilled from the observability-and-instrumentation skill (MIT). Method in our own words; the full process lives in that source. Use when adding logging, metrics, tracing, or alerting, or when shipping any feature that runs in production.

## The process
1. **Define "working" before instrumenting.** Write down what correct behaviour looks like — the numbers, the latencies, the error rates — before adding a single log line. Instrumentation without a definition of working measures noise.
2. **Pick the right signal for each question.** Logs answer "what happened"; metrics answer "how much and how often"; traces answer "where did the time go". Do not force one signal to do another's job.
3. **Structured logging.** Logs are events with fields (request id, user id, outcome), not free text. A log line a machine cannot parse is a log line nobody will query.
4. **Metrics.** Counters for events, gauges for current state, histograms for latencies. Every metric has an owner and a reason; a metric nobody alerts on or graphs is clutter.
5. **Distributed tracing.** A trace follows a request across services, with one trace id end to end. Trace the boundaries, not every function.
6. **Alerting.** Alert on symptoms users feel (error rate, latency), not on causes (CPU). Every alert has a runbook: what it means, how to check, what to do. An alert with no runbook is a page nobody can answer.
7. **Verify the telemetry itself.** Telemetry that is never checked is telemetry that is broken silently. After shipping, confirm the logs arrive, the metrics move, and the alert fires when it should (test the alert, do not trust it).

## Runbooks
A runbook names the symptom, the checks in order, and the actions with their rollback. Write the runbook before the alert goes live; the person paged at night should not have to invent it.

## Rationalizations — do not accept these
- "We will add logging later" — later is when the incident happens, and then it is too late.
- "Console output is enough" — console output that nobody collects is not observability.
- "Too many alerts is fine, we ignore the noisy ones" — ignored alerts train the team to ignore the real ones. Fix or delete the noisy alert.

## Red flags
- A production feature with no metric that says whether it works.
- Logs containing secrets or personal data.
- An alert that has never fired in testing and has no runbook.
