---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  A pass run with a tool deliberately withheld writes a run record whose
  tool-surface block names that tool as expected-and-absent; the same pass run
  with the full surface names it as present. Both records are produced without
  any tool being consulted twice, and a pass that cannot determine its surface
  writes that it could not rather than omitting the block.
instrument: npx vitest run test/loop/run-record-tool-surface.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** The parent's stated cost is "very small — the facts are available at startup; only the writing is missing." That is a claim about the runtime, and it has an exit code.

**The assumption under test.** That a pass can determine its own tool surface at start, and that the determination is honest in the case that matters — a tool that was *expected* and is absent, which is the case the record exists for. A block that lists what resolved is easy and nearly useless; the diagnostic value is entirely in naming the gap, and naming a gap requires knowing what was expected, which is the half nothing currently holds.

**Why this is not the test already attached.** "Hand a reader five run records and ask which passes did their job" asks whether the block changes a reader's conclusion — two humans, half an hour, and it does not need this built. It is the right test of whether the record is *worth* writing. It is not a test of whether the record can be written correctly, and the parent's own evidence shows the failure mode is silent rather than unconvincing: four filings converged on the right cause only after three wrong ones, because no record of the capability existed at all.

**What is red today.** No pass writes a tool-surface block. The failure is a missing mechanism rather than a wrong one, which is the weaker kind of red, and it is stated here plainly rather than dressed up: the spec's assertions describe a block whose shape does not exist, so the first thing it does is fail to find one. What keeps it from being merely "create this file" is the second half of the threshold — the withheld-tool case and the cannot-determine case — which a naive implementation that lists whatever resolved will fail.

**What a green result does NOT settle.** Everything the parent says it does not settle. The pass still burns its compute producing nothing; nobody is made to read the record; and on a schedule nobody reads, a correct block changes exactly nothing. Feasibility answered mechanically leaves the usability question where it was, and the sibling reader test is the one that answers it.

**Kinship worth honouring in the build.** The parent notes this is the same defect and the same fix as "Every recorded step carries the directory and argv it actually ran with" — a record honest about its outcome and silent about the one variable explaining it. If either is built the other is nearly free, and this instrument should probably be written so that it does not foreclose sharing the mechanism.

**Lane: compute-only.** A pass run twice against a fixture vault, once with a tool withheld; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass. Nothing here was run.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/run-record-tool-surface.test.ts` — No test files found, exiting with code 1
