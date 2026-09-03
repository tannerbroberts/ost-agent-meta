---
type: AssumptionTest
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/loop/compute-lane-runner.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (desirability/feasibility):** a meaningful share of the existing 66-test backlog is genuinely compute-only, and running that lane produces decisive verdict drafts rather than mush.

**Method:** classify all 66 tests into the three lanes; execute every compute-only test against existing data (vault git histories, run journals, inbox state); draft supported/refuted verdicts with the evidence inline. The operator reads the drafts and records or rejects each with one pre-filled command.

**Pre-committed threshold:** >= 3 compute-only tests produce decisive drafts the operator records unchanged, and >= 1 produces a KILL (a refuted verdict that defers a solution). Zero kills means compute-only tests only ever confirm — decoration, not discovery.

**Decides:** whether the triage lane is real, and calibrates what share of this tree's work was ever actually blocked on human hours.

*Proposed by the agent — verdicts recorded only by a human via ost-agent result.*

## History
- 2026-08-05 instrument: (none) → npx vitest run test/loop/compute-lane-runner.test.ts — Asserts a compute-only lane runner exists that executes every test carrying lane: compute-only against existing vault data and emits a verdict draft with the evidence inline and a pre-filled ost-agent result line. Run against a seeded fixture holding known compute-only tests, so it cannot pass vacuously on the empty live set — the positive-control discipline this vault learned from the planted-instance run. Red today because the runner is the half deliberately not built: v0.6.0/v0.7.0 shipped the lane model, the report and the setter, and this node's own build notes state that compute running the compute-only lane unprompted is not implemented and that the runnable set is empty by construction.

## What the instrument does not settle

`npx vitest run test/loop/compute-lane-runner.test.ts` settles only that the lane can be executed and a draft produced. It says nothing about either half of this test's pre-committed threshold, and the gap is worth stating because a green runner will look like the test passed.

The bar is **≥3 drafts the operator records unchanged, and ≥1 KILL**. "Records unchanged" is a person's judgement about whether a draft was decisive or mush — the exact thing the assumption doubts — and no exit code observes it. The KILL requirement is stronger still: it asks whether compute-run tests ever *refute* anything or only ever confirm, and a runner that emits three confident supported-verdicts would satisfy the instrument while demonstrating precisely the decoration this test was written to detect.

There is also a prerequisite the instrument cannot supply. The runnable set is empty by construction — only a human's `ost-agent lane --set` moves a test into `compute-only`, and nothing has. So a green runner executes zero live tests until someone triages the backlog; the fixture proves the mechanism, not that there is any work for it to do.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/compute-lane-runner.test.ts` — No test files found, exiting with code 1
- 2026-09-03 **green** (exit 0) `npx vitest run test/loop/compute-lane-runner.test.ts` — Duration  457ms (transform 118ms, setup 0ms, collect 177ms, tests 45ms, environment 0ms, prepare 37ms) [spec 9d75e6cfb1d3]
