---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Every consumer found is one that could honour the flag, and the total is at
  most 12.
instrument: npx vitest run test/ost/retraction-consumers.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that retraction can actually be made total — that every place which counts, scans, gates, or lists nodes can be found and taught to exclude a retracted one. A single reader that forgets makes retraction worse than nothing, because the node then looks handled while still being counted.

**Risk category: feasibility.** Whether the set of consumers is enumerable and small enough to change confidently.

**Design.** Before building anything, enumerate every code path that reads nodes — the sweep, each gate, the duplicate scan, the counts, the status rollup, the debt report, the check invariants — and for each, determine whether it could honour an exclusion flag and what it would take. Produce the list with a verdict per entry.

**Why it is small.** It is a read of the codebase, needs no new code, and answers the question that decides whether the solution is buildable at all.

**What it will not cover.** It says nothing about consumers added later, which is the real long-term risk — a reader written next year will not know retraction exists unless something enforces it.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/retraction-consumers.test.ts — The threshold — every consumer found is one that could honour the flag — is settled by a spec that plants one retracted node and asserts each node-reading path (check, debt, status rollup, duplicate scan, the sweep, each gate) excludes it, which turns "could honour" into "does honour". It fails today because retraction does not exist.
