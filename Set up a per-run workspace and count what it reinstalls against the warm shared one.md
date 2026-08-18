---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  A per-run workspace reinstalls zero packages and costs at most 20% more
  wall-clock to prepare than reusing the warm shared path. Failing either bar
  refutes affordability at hourly cadence and this candidate loses to leasing.
instrument: npx vitest run test/runner/per-run-workspace-cost.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What this measures.** Prepare a workspace twice — once at the fixed shared path with its symlinked dependency tree, once at a path derived from a run id — and compare package installs performed and wall-clock elapsed. The claim under test is that uniqueness of the working tree does not force re-acquisition of the dependency tree.

**The bar, pre-committed.** Stated in the threshold above. Zero reinstalls is the hard half; the 20% wall-clock allowance exists because a per-run path must still create a directory and a link, and that is real work that should not count as refutation.

**Why it should be red today.** There is no per-run path to prepare. Setup derives a single fixed location — `/tmp/ost-main` in the observed trace — so nothing exists to measure the comparison against, and a spec asserting two distinct prepared workspaces has no second workspace to find.

**Honesty about that claim.** As with its siblings, this pass could not verify it against the repository: product-directory reads were denied and `ost_read_repo` was not granted. The red-today claim comes from the transcript, which shows the fixed path and the `ln` into it, not from the code. A builder should expect the first failure to be the missing spec file and the second to be the missing per-run derivation.

**What a green run does NOT settle**, and this is the important part. It measures cost and nothing else. The assumption's own body names a failure that a timing test structurally cannot see: two live per-run worktrees symlinking one shared `node_modules` are isolated in their working trees and not isolated at all in their dependencies, so runs on branches with different requirements would overwrite each other's packages while every number this test reports stays green. Passing this bar licenses the cost argument only, and leaves the correctness-under-concurrency argument entirely open. Nor does it touch whether leaked workspaces accumulating in `/tmp` are acceptable to an operator, which is the quiet leak this candidate trades the loud failure for.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/per-run-workspace-cost.test.ts` — No test files found, exiting with code 1
- 2026-08-18 **green** (exit 0) `npx vitest run test/runner/per-run-workspace-cost.test.ts` — Duration  1.92s (transform 15ms, setup 0ms, collect 14ms, tests 1.71s, environment 0ms, prepare 25ms)
