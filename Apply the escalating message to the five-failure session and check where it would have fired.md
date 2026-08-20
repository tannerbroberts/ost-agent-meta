---
type: AssumptionTest
status: deferred
created: '2026-08-03'
evidence: assertion
threshold: >-
  The counter fires by the second occurrence in both replays, and 3 of 5 live
  sessions change approach rather than retrying.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that escalated wording changes what the caller does next. It arrives after the damage has begun by construction, and it can only change framing rather than actually helping — so the question is whether framing is enough.

**Risk category: usability.**

**Design.** Take the session with five identical shell failures and the one with three. Replay them against the counter and record where it would have fired and what it would have said. Then put the escalated message in front of a fresh session facing the same failure and see whether it changes approach or retries the same form.

**Why it is small.** The replay is mechanical against a corpus that exists; the live half is a handful of sessions.

**What it will not cover.** A session shown an unusual message may change approach because it is unusual rather than because it is right, and novelty wears off. It also cannot tell whether the new approach is better.

A human reads the outcome and records the result.

## Issues
- 2026-08-04 2026-08-04 (unattended sweep) Left un-instrumented on purpose: this test names two lanes in one threshold, and instrumenting it would quietly answer the cheap half and let a reader take that for the whole. "The counter fires by the second occurrence in both replays" is mechanical — a replay over a corpus already on disk, settled by a spec. "3 of 5 live sessions change approach rather than retrying" is not: it measures what a caller does when shown a message, which is the assumption the solution actually rests on, and the node itself says "a human reads the outcome and records the result". A single command cannot come out a failure on the second clause, so attaching one would produce a green that means the counter counts — a fact nobody doubted — while the load-bearing question stays untouched. For a human: split this into a replay test (instrumentable now) and a live-session test (humans-required), or restate the threshold on the clause you actually want gated. I could not do either — creating the split node is out of this sweep's scope and `ost_flag_humans_required` is not granted on this surface.

## History
- 2026-08-20 status: unvalidated → deferred — Split rather than instrumented. This test named two lanes in one threshold — a replay any spec can settle, and a live-session measure only a person can make — and its own 2026-08-04 Issues entry asked for the split. The 2026-08-20 unattended sweep created the two halves beside it under the same assumption: "Replay the five-failure and three-failure sessions through the class counter and require it to fire by the second occurrence in both" (compute-only, instrument npx vitest run test/loop/repeat-class-escalation.test.ts) and "Show the escalated message to five fresh sessions facing the same failure and count which change approach" (humans-required). Deferred means superseded by those two, not abandoned; its design paragraph is preserved in both.
