---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: The operator visits at least twice in 4 weeks and the total does not grow.
instrument: npx vitest run test/ost/pending-ask-queue.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the operator visits the queue. Queues that are never emptied become furniture, and if the ask rate exceeds the visit rate for long, the operator gets a large number where they used to get a small surprise.

**Risk category: usability.**

**Design.** Assemble the queue from what is already outstanding in this vault — the tests awaiting a person, the annotations awaiting a ruling. Present it with ages. Over four weeks, record every visit, how many items were cleared, and how the total moved. The direction of the total is the finding.

**Why it is small.** The backlog exists; assembling it is a query. The measurement is a count per week.

**What it will not cover.** A queue seeded with a large existing backlog is discouraging in a way a queue that grew from empty would not be. This is close to the worst case for adoption, which cuts both ways as a test.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/pending-ask-queue.test.ts — Asserts the two properties that separate this from what already ships: an ask raised mid-pass by one run is still in the queue on a later run, carrying a non-null age and the command that would clear it. Red against today's code rather than merely against a missing file — outstandingAsks exists but is derived only from blockedOnPermission tests, so an ask a run could not answer itself is never persisted and reports ageDays null.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/pending-ask-queue.test.ts` — No test files found, exiting with code 1
- 2026-08-11 **green** (exit 0) `npx vitest run test/ost/pending-ask-queue.test.ts` — Duration  2.24s (transform 133ms, setup 0ms, collect 200ms, tests 1.86s, environment 0ms, prepare 26ms)
