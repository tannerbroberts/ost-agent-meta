---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  Files five or fewer records in total, and both the repeated refusal and the
  repeated poll appear as single records carrying their count and span.
instrument: npx vitest run test/adapters/recurrence-rule-filing.test.ts
authorship: machine
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that repetition is a good enough proxy for significance, and that grouping "the same error shape" can be done mechanically. The second half is the harder one — ten sessions saying `== not found` are obviously the same shape, but thirteen blocked sleep-then-poll calls differ in their sleep durations and their target commands.

**How it would run:** apply the rule to the same 29 records used for the surface rule, so the two candidates are judged on identical material. Record how many records it files, and whether the two known patterns — the repeated refusal and the repeated poll — each surface as one record carrying their count and span.

**What decides between this and the surface rule:** not the raw hit rate, but whether this one keeps the patterns the other discards while still filing few enough records that a pass can read them all.

Retrospective, no build. Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/adapters/recurrence-rule-filing.test.ts — The threshold is two mechanical clauses over a fixed corpus — files five or fewer records in total, and both the repeated refusal and the repeated poll appear as single records carrying their count and span — so the spec replays the same 29 harvested records through the recurrence rule and asserts the filed count and the two known groupings, including that thirteen blocked sleep-then-poll calls with differing durations and targets collapse to one record. It fails today because no recurrence rule exists.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/adapters/recurrence-rule-filing.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/adapters/recurrence-rule-filing.test.ts` — Duration  418ms (transform 40ms, setup 0ms, collect 55ms, tests 106ms, environment 0ms, prepare 35ms)
