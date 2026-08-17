---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/disconfirmer-ordering.test.ts
---
#AssumptionTest #unvalidated #viability #evidence/assertion

**Assumption under test:** That ordering by time-to-kill actually shrinks the set faster than testing by importance — the whole economic claim of the solution.

**Design:** Take two comparable branches; test one in importance order, the other in cheapest-disconfirmer order, for a fixed effort budget. **Pre-committed threshold:** the disconfirmer-ordered branch eliminates at least twice as many candidates for the same hours. Anything less and the reordering is not worth the counter-intuitiveness.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/ost/disconfirmer-ordering.test.ts — Asserts the inversion this node's whole idea rests on: the test queue orders by expected candidates-eliminated-per-effort, not by importance, and a fixture where the two orderings disagree comes out in the disconfirmer order. Red today because the queue has no ordering at all beyond the lane it sorts by.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/disconfirmer-ordering.test.ts` — No test files found, exiting with code 1
- 2026-08-17 **green** (exit 0) `npx vitest run test/ost/disconfirmer-ordering.test.ts` — Duration  217ms (transform 15ms, setup 0ms, collect 12ms, tests 7ms, environment 0ms, prepare 27ms)
