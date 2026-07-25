---
type: AssumptionTest
status: unvalidated
evidence: assertion
source: 'agent:P4_assumptions'
created: '2026-07-24'
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
