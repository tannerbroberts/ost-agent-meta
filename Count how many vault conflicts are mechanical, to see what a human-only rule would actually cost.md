---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At most 5 mechanical conflicts per genuinely contested one, and under 3
  escalations per week.
instrument: npx vitest run test/git/conflict-mechanicality-census.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that conflicts needing human judgement are common enough to justify sending all of them to a person. Most conflicts in an append-only Markdown vault are mechanical, and a rule treating all of them as human-only will send a great deal of trivia to an operator who will stop reading it.

**Risk category: viability.**

**Design.** Generate realistic conflicts by replaying concurrent work against both existing vaults. Sort each into mechanical — two appends to different sections, a link added on both sides — or genuinely contested. Compute the ratio, and estimate how many of each an operator would see per week at current activity.

**Why it is small.** Replaying against existing history, no build, and the output is a ratio and a rate.

**What it will not cover.** The mechanical/contested line is drawn by a person who may be more confident than a rule could be. Where they hesitate is worth recording separately, since those are the cases that decide the boundary.

Setting this boundary is a human's decision. A human runs this and records the result.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/git/conflict-mechanicality-census.test.ts — Classifies every conflict in the vault history as mechanically resolvable or not, which is the cost the human-only rule would incur; fails today because no classifier exists to count them.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/git/conflict-mechanicality-census.test.ts` — No test files found, exiting with code 1
- 2026-08-26 **green** (exit 0) `npx vitest run test/git/conflict-mechanicality-census.test.ts` — Duration  430ms (transform 46ms, setup 0ms, collect 50ms, tests 26ms, environment 0ms, prepare 74ms)
