---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/eval/canary-parallel-run.test.ts
---
#AssumptionTest #unvalidated #usability #evidence/assertion

**Assumption under test (usability, with feasibility riding along):** A human can look at old-process output beside new-process output and tell which is better, quickly and consistently — otherwise the comparison produces cost without a decision.

**Proposed test:** Take one real workflow change, produce three output pairs over the same inputs, and give them to three reviewers independently. Time each judgement.

**Size:** one duplicated pass plus three short reviews.

**Pre-committed threshold:** each pair decided in ≤5 minutes AND ≥2 of 3 reviewers pick the same winner on all three pairs. Split verdicts mean the diff is not legible and the canary is decoration.

**Decides:** whether canarying can gate real workflow changes, or only changes with crisply comparable output.

Proposed by the agent — to be run by human reviewers; the agent must not judge its own output pairs. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/canary-parallel-run.test.ts — Asserts the property the node claims as its whole advantage — no interruption, because the old process never stops: both processes run over identical input, both outputs are captured for comparison, and a canary that errors or diverges leaves the incumbent's result untouched. Red today because no canary harness exists and a changed process simply replaces the old one.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/eval/canary-parallel-run.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/eval/canary-parallel-run.test.ts` — Duration  214ms (transform 17ms, setup 0ms, collect 14ms, tests 3ms, environment 0ms, prepare 25ms)
