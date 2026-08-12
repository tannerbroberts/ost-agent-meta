---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  A shipped solution with no recorded run appears in a queue that asks for an
  observation, never in `solutionsMissingInstruments`, and the write boundary
  accepts a green command for it while still refusing one for an unshipped
  solution.
instrument: npx vitest run test/ost/shipped-observation-queue.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Who runs it.** An attended session with a build environment, or a human. This pass could not set a lane label — that is a human's `ost-agent lane --set`.

**What this measures.** Whether the two queues can coexist without the acceptance rules bleeding into each other. Fixture: one shipped solution with no recorded run, one unshipped solution with a prose-only test. Assert the shipped one is asked for an observation and the unshipped one for a red-now instrument, then assert the write boundary accepts a passing command for the first and still refuses one for the second.

**The bar, pre-committed.** All four assertions hold. The fourth is the one that matters — if relaxing the red-now rule for shipped work also relaxes it for unshipped work, this solution has broken the single property that makes an agent-authored instrument worth anything, and should be abandoned rather than repaired.

**Why it is red today.** There is one queue and one acceptance rule. `ost_set_instrument` refuses anything that is not a spec-shaped command and the tool documents the red-now requirement without exception, so there is no path by which a green command is accepted for anything. Both the second queue and the conditional acceptance are absent from today's code, and the spec's assertions fail against the mechanism rather than against a missing file.

**What a green run does NOT settle.** It shows the plumbing separates cleanly. It does not show that a green spec is *meaningful* evidence a shipped mechanism is present — that is this test's own parent assumption, and it turns on whether the spec was written from the mechanism or from the node's prose, which no spec can check about itself. Nor does it show anyone wants shipped work to keep costing them attention.

## History
- 2026-08-06 body edited — The body declared "Lane: compute-only", which this pass had no power to set — `ost_flag_humans_required` is withheld on this surface and only a human's `ost-agent lane --set` moves what compute may run. The node carries no `lane:` field, so its effective lane is needs-humans (confirmed: it landed in `assumptionWork.needsHumans`), and the prose contradicted that. Replaced with the vault's established "Who runs it" phrasing.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/shipped-observation-queue.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/ost/shipped-observation-queue.test.ts` — Duration  3.52s (transform 139ms, setup 0ms, collect 209ms, tests 3.11s, environment 0ms, prepare 30ms)
