---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/eval/adversarial-critic-invariants.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability, with a usability constraint):** An independent critic surfaces objections a human agrees are worth acting on — and few enough of them to read.

**Proposed test:** Run one critic pass over the current opportunity set. Hand a human the raw list, unfiltered, and have them mark each objection "worth acting on" or "noise" without seeing which node it came from.

**Size:** one pass of compute plus 30 minutes of rating.

**Pre-committed threshold:** ≥40% of objections rated worth acting on AND the total list is ≤20 items. A high hit rate buried in 60 objections fails — an unread critic is not a critic.

**Decides:** whether adversarial review earns a standing slot in the maintenance loop.

Proposed by the agent — the rating must be done by a human; the agent must not grade its own critic. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/adversarial-critic-invariants.test.ts — Asserts the two invariants that define this candidate rather than its siblings: a critic pass creates no nodes and removes nothing, and every objection it emits names the evidence that would settle it. Red today because no critic pass exists, so nothing enforces that a reviewer which only lowers unearned confidence cannot quietly author or delete.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/eval/adversarial-critic-invariants.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/eval/adversarial-critic-invariants.test.ts` — Duration  356ms (transform 73ms, setup 0ms, collect 110ms, tests 12ms, environment 0ms, prepare 26ms)
