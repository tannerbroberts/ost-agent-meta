---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 20% of new nodes ladder to something under the real goal other than
  the milestone.
instrument: npx vitest run test/ost/milestone-under-outcome.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that an unreachable root keeps working on the reader. A goal nothing beneath it can reach may simply be ignored, and a milestone that absorbs all the attention is functionally the outcome regardless of where it is filed.

**Risk category: usability.**

**Design.** In a second vault, set the root to the goal actually wanted and hang the affordable one beneath it as a labelled milestone. Run it for a quarter. Then count: how many nodes ladder to the milestone, how many to anything else under the real goal, and how often the real goal is referred to in any pass note or annotation.

**Why it is small.** It is a filing arrangement, not a build. The counting is mechanical at the end.

**What it will not cover.** A quarter in one vault run by the person who proposed the arrangement. Nothing here isolates the labelling from the operator's intent to make it work.

The outcome is human-set. Nothing in this test may be run by a pass, and no pass may change a root.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/milestone-under-outcome.test.ts — Counting what laddered up to the real goal presumes the tree can hold both goals at once — the real one at the root and the affordable one beneath it as a milestone — and today it cannot: the root takes one Outcome and everything below is an Opportunity. This asserts the structure the count depends on: a milestone attaches under the Outcome and is distinguishable from a category bucket, every node rolls up through its milestone to the root goal, and the rollup reports per-milestone as well as per-bucket so "what laddered up" is a number the tree computes rather than a person tallies. Missing-spec red, not assertion red — no milestone layer exists, so this fails on a missing file; a builder should write it against the real hierarchy check so it goes red on the refused milestone edge. It does not settle the test's own question, which needs a quarter to elapse and a human to read the result.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/milestone-under-outcome.test.ts` — No test files found, exiting with code 1
