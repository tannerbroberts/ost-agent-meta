---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 60% of the would-be-grandfathered nodes were brought into compliance
  within a month.
instrument: npx vitest run test/ost/grandfathered-backlog-replay.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a grandfathered backlog eventually gets cleared rather than sitting forever. Exempting by date removes all pressure, and if the point of tightening was that the old nodes were genuinely a problem, a permanent exemption answers the wrong complaint.

**Risk category: viability.**

**Design.** Identify the last three times a rule tightened in this project. For each, count how many existing nodes would have been grandfathered, and check how many of those have since been brought into compliance by any means. Compute the clearance rate and the time it took.

**Why it is small.** The rule changes and the node history are both in the commit log.

**What it will not cover.** These tightenings happened without grandfathering, so nodes were under pressure from a red gate. Clearance under that pressure is an upper bound on what would happen with the pressure removed — which makes a low number here decisive and a high number weak.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/grandfathered-backlog-replay.test.ts — Replays the last three tightenings and asserts the nodes marked as predating each one were subsequently brought into compliance rather than accumulating; fails today because nothing marks or tracks a grandfathered node.
