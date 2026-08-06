---
type: AssumptionTest
created: '2026-08-06'
evidence: assertion
threshold: >-
  Recomputed entered/left sets match the pass's recorded actions exactly; any
  divergence refutes recomputation.
instrument: npx vitest run test/ost/queue-delta-from-git.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption under test (feasibility).** That a past pass's queue can be recomputed from git rather than stored, because every mutation auto-commits and the tree at any commit fully determines the queue.

**The test.** Check out the vault at two commits that bracket a known pass, compute `next_work` over each, and diff. Assert the recomputed "before" queue matches what that pass actually acted on — the 2026-08-05 sweep is a usable specimen, since its four status corrections are in the History lines it wrote.

**Pre-commit before running:** the recomputed entered/left sets must match the pass's recorded actions exactly. Any divergence refutes recomputation and means the delta needs stored state, which changes the solution's cost.

**What this does NOT settle.** Whether a delta changes what an operator does. A correct number nobody acts on is the failure mode the sibling node names, and only an operator reading one reports on it.

**Lane: compute-only.**

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/queue-delta-from-git.test.ts` — No test files found, exiting with code 1
