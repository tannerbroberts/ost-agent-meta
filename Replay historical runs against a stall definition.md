---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/loop/stall-definition-replay.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** "Making progress" can be defined crisply enough to distinguish a stalled pass from a slow one — the difference between a useful watchdog and one that kills healthy work or restarts broken work forever.

**Proposed test:** Write down a candidate definition of progress. Replay ten recorded runs against it — including the ones already known to have stalled — and see what it would have flagged.

**Size:** an hour, offline, against runs that already happened.

**Pre-committed threshold:** every known stall detected AND zero false alarms on the healthy runs. One false restart of healthy work is worse than no supervisor, because it burns compute while looking alive.

**Decides:** whether automatic restart is safe to attempt, or whether liveness should only be reported to a human.

Proposed by the agent — to be run by a human against recorded runs. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/loop/stall-definition-replay.test.ts — The threshold is a confusion matrix over runs that already happened — "every known stall detected AND zero false alarms on the healthy runs" — and the runs are on disk in `.ost-agent/runs/`, so the measurement is a replay rather than an observation anyone has to make. The spec applies a candidate progress definition to every recorded run journal, asserts each known stall is flagged, and asserts no healthy run is. It fails today because no stall definition exists in the repository: nothing distinguishes a pass making slow progress from one that has stopped, which is exactly the gap the node names. Note what a green here would and would not license — it decides whether liveness can be *detected* from journals as they stand, not whether automatic restart is safe, since a correct detector attached to an unsafe restart still burns compute while looking alive.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/stall-definition-replay.test.ts` — No test files found, exiting with code 1
- 2026-09-02 **green** (exit 0) `npx vitest run test/loop/stall-definition-replay.test.ts` — Duration  234ms (transform 18ms, setup 0ms, collect 17ms, tests 7ms, environment 0ms, prepare 28ms) [spec 5a0981b93bda]
