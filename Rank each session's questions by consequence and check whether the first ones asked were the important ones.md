---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The most consequential question is in the first half of the order asked in at
  least 3 of 4 sessions.
instrument: npx vitest run test/loop/question-budget-ordering.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a run can rank its questions before it has seen them all. A budget spent on the first three of seven, defaulting on the most important, is worse than no budget at all.

**Risk category: feasibility.**

**Design.** Take four sessions with multiple clarifying questions. For each, have a person rank the questions by consequence with full hindsight. Then check where the most consequential one fell in the order it was actually asked. If the important question is reliably late, a budget spent in order will miss it.

**Why it is small.** Four sessions already harvested, one ranking each.

**What it will not cover.** The order questions were asked reflects an agent that was not rationing. One that knew it had a budget might have held back, and this cannot see that counterfactual — though it does establish whether asking in arrival order is safe.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/question-budget-ordering.test.ts — Replays the four harvested sessions' clarifying-question sequences against the budget's ranking function and asserts the hindsight-top question falls inside the spent half in at least 3 of 4 — the threshold's own arithmetic, mechanised. Red today because neither a question budget nor a ranking function exists anywhere in the loop, so there is nothing for the spec to call.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/question-budget-ordering.test.ts` — No test files found, exiting with code 1
