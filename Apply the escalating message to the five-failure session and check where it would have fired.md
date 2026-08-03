---
type: AssumptionTest
status: unvalidated
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
