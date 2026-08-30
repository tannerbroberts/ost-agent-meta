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
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-29 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-30 **no-spec** (exit none) `npx vitest run test/evidence/dispose-solution-instrument-bucket.test.ts` — test/evidence/dispose-solution-instrument-bucket.test.ts does not exist — no spec was collected, so nothing was measured

## What a disposition would actually park, measured rather than assumed (2026-08-30 unattended sweep)

This node's closing paragraph names its own weakest point: a green proves the wiring, and "that anyone will ever file such a disposition" stays untested. This pass did not settle that — it is a person's willingness and no spec reaches it — but it did measure the thing that decides whether filing one would be worth anyone's minute, which nothing had counted.

**The measurement.** `solutionsMissingInstruments` stood at **66** this firing, capped to 25 shown. Six of the 25 were read in full and classified by whether the node itself already says an instrument does not belong:

| Solution | What the node already says |
|---|---|
| A human-edited manifest of loop-prescribed call sequences the harvester suppresses | "There is deliberately no instrument here" — plus a lane note recording it was created humans-required |
| An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target | "No command: this one is humans-required on purpose" |
| A repeated wait on the same condition resumes and doubles its budget automatically, up to a ceiling set once by hand | "No instrument. The helper is on the session's PATH and supplied by the harness, not in this repository" |
| Maintain a running per-item task list the next pass reads before reconstructing state itself | "Deliberately left prose-only; not a skipped step" |
| Remote push optional and off by default | "do not write an instrument here" — the mechanism ships and is pinned by green specs |
| Name the specific mechanisms a hand process structurally cannot have | the softest of the six: it never says "no instrument" in those words, but its open assumption is whether practitioners recognise the pitch, which its own audit section says needs people |

**Six of six**, with the sixth qualified as above. Every one of them carries a prior sweep's dated section explaining the abstention, so the answer was not merely derivable — it was already written on the node, by an earlier firing that paid to derive it.

**Why that number is the case for this test rather than a complaint about the bucket.** The re-read cost is not paid once. A bucket entry that cannot be retired is re-offered to every firing, and a firing has exactly two moves available: re-read the node and re-confirm the abstention (what this pass did, at roughly a thousand tokens a node), or skip it unread and lose the ability to tell a deliberate abstention from a genuinely un-instrumented solution. There is no third move, because `ost_flag_humans_required` is withheld on the unattended surface and no agent tool records "correctly has no instrument". If the 6-of-6 rate holds across the other 41 entries, this bucket is close to entirely audited already, and what it costs from here is re-derivation of a settled answer, forever.

**The honest limit on extrapolating it.** Six of 25 shown, and the 25 are the head of 66 — this is a sample from a cap, not a census, and the cap is unfiltered so the sample is not random either. It bounds nothing about the 41 unseen entries. What it does establish is that the abstention case is common enough to be the first thing a reader hits, which is the premise this test's fixture assumes when it seeds three such solutions.

**One first-party observation about the route being unbuilt, which is why the cost recurs.** `withheldByDisposition` came back `[]` on this firing — this vault holds no live disposition of any kind. And this test's own `## Instrument Log` now carries **six consecutive `no-spec` runs** of the same command (five on 2026-08-29, one on 2026-08-30), each recording that `test/evidence/dispose-solution-instrument-bucket.test.ts` does not exist. So the solution face of the disposition ledger is unbuilt, has been re-checked once per firing since it was proposed, and the re-read cost above is what accrues in the meantime. That re-checking is deliberate — `runInstrument` short-circuits on the missing file so the queue costs nothing to re-run — but the log it writes to is a reserved section that grows by one identical line per pass, which is a small cost nobody has counted either.

**What this does not change.** No instrument was set, no threshold moved, no lane labelled, and this test's verdict is exactly as open as it was. Nothing here bears on the larger half the node already names: whether an operator files a disposition once the wiring exists.

_Method: this firing's own `ost_next_work` response, plus six `ost_read_tree` node reads. No test was run and no result is recorded. Grounds feasibility and cost only — silent on desirability. Rung unchanged at the `assertion` floor._
