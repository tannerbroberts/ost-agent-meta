---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least half of the failed calls came from a caller showing prior signs of
  doubt.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that callers know when they are uncertain. A validate-only twin helps only someone who thinks to use it, and the evidence points the other way: three identical rung refusals in one day suggests a caller who was confident and wrong, not one who was hesitating.

**Risk category: usability.**

**Design.** Take every failed call in the usage traces. For each, read the surrounding session record and judge whether the caller showed any sign of doubt beforehand — a hedge, a check, a question. Count how many failures came from a caller who would plausibly have chosen to validate first.

**Why it is small.** The traces and the transcripts both exist; this is reading them against each other.

**What it will not cover.** Judging doubt from a transcript is imprecise, and a caller who would validate reflexively before every risky call is not the same as one who felt uncertain. Both readings are worth recording separately.

A human runs this and records the result.
