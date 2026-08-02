---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  Files five or fewer records in total, and both the repeated refusal and the
  repeated poll appear as single records carrying their count and span.
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that repetition is a good enough proxy for significance, and that grouping "the same error shape" can be done mechanically. The second half is the harder one — ten sessions saying `== not found` are obviously the same shape, but thirteen blocked sleep-then-poll calls differ in their sleep durations and their target commands.

**How it would run:** apply the rule to the same 29 records used for the surface rule, so the two candidates are judged on identical material. Record how many records it files, and whether the two known patterns — the repeated refusal and the repeated poll — each surface as one record carrying their count and span.

**What decides between this and the surface rule:** not the raw hit rate, but whether this one keeps the patterns the other discards while still filing few enough records that a pass can read them all.

Retrospective, no build. Proposed by the agent; a human runs it and records the outcome.
