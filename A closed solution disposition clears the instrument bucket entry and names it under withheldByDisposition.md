---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  at least 3 of 3 disposed solutions leave the bucket and at least 3 of 3 appear
  under withheldByDisposition
instrument: npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A fixture vault, a ledger write and an assertion about a response — all artifacts already on disk or created by the spec itself.

**What the spec must assert, modelled on the one that already ships.** `test/evidence/corroborate-disposition.test.ts` pins the same contract for the evidence face and is the template: seed a fixture vault with three solutions whose tests are prose only, append a `closed` disposition of kind `solution` for each subject title via `appendDisposition`, then call `computeNextWork` and assert (1) all three leave `solutionsMissingInstruments`, (2) all three are named under `withheldByDisposition` with the list field reading `solutionsMissingInstruments`, (3) the node files are byte-identical afterwards, so a disposition parks work without touching the tree, and (4) a subsequent `reopened` entry puts all three back on the bucket.

**Assertion four is the one worth insisting on.** Reversibility is rule 3 in the ledger's own docstring — "an irreversible hide is the mirror image of the unclearable red this repository keeps re-learning" — and it is the assertion a builder wiring up a single `omitDisposed` call would most plausibly leave untested, because the reversal comes free from the shared helper right up until someone caches something.

**Why it fails today, stated honestly.** `test/evidence/dispose-solution-instrument-bucket.test.ts` does not exist, so this run is filed `no-spec` and mints no permit — the same weak red as its siblings this pass, for the same reason: authoring a spec file is outside what this surface can do. The named template file, the four assertions and the exported functions (`appendDisposition`, `omitDisposed`, `computeNextWork`) are what let the builder write an assertion rather than reconstruct the question.

**What a green would NOT settle, and it is the larger half.** That anyone will ever file such a disposition. `dispose` is a human's CLI command by design and this vault holds zero live dispositions while its evidence queue has been drainable by that exact route for weeks. This test proves the wiring; the operator's willingness to use it is untested and untestable here.

## Instrument Log
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured
