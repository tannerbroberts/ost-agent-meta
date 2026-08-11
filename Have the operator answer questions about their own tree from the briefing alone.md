---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 7 of 10 correct, including catching at least 1 of the 2 seeded
  errors.
instrument: npx vitest run test/ost/standing-briefing.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that reading a briefing maintains real understanding rather than the feeling of it. The operator may end up holding the agent's picture of the tree instead of their own, and if the agent has misread it the briefing will misread it identically and confidently.

**Risk category: usability.**

**Design.** After the operator has read only the briefing for a month, ask them ten questions about their own tree that the briefing does not directly answer — which branch has the weakest evidence, what would change if a named assumption failed, which two opportunities are closest to duplicates. Grade against the tree. Seed two questions where the briefing is known to be wrong or thin, and see whether the operator notices.

**Why it is small.** Ten questions after a month of a briefing that is a by-product of passes already happening.

**What it will not cover.** Answering questions is not the same as being able to make good decisions, and one operator's month is a thin sample.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/standing-briefing.test.ts — Asserts the briefing is regenerated in full each pass and names the belief the tree currently rests on — the weakest rung of the believability rollup — so a cold reader gets the tree's actual footing rather than a diff. Red today because no standing briefing is generated at all.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/standing-briefing.test.ts` — No test files found, exiting with code 1
- 2026-08-11 **green** (exit 0) `npx vitest run test/ost/standing-briefing.test.ts` — Duration  314ms (transform 73ms, setup 0ms, collect 111ms, tests 7ms, environment 0ms, prepare 26ms)
