---
type: AssumptionTest
status: unvalidated
created: '2026-08-06'
evidence: assertion
threshold: >-
  All three firings show fewer than 10 unrelated output lines in the surrounding
  window; 10 or more for any one of them falsifies the content hypothesis for
  that firing.
instrument: npx vitest run test/telemetry/gate-signal-density.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** How much output surrounded a line in a recorded session is a count over a file, and nobody's recollection improves on it.

For each of the three recorded firings, measure the density of unrelated output around it: how many non-gate lines fell inside the window immediately before and after, and how many other lines separated it from the next thing the reader had to decide. Report all three, not an average — the interesting outcome is if they disagree, because one buried firing and two isolated ones would mean neither hypothesis explains all three and the node needs re-cutting.

**Pre-committed bar:** the content hypothesis survives only if all three fired with fewer than 10 unrelated output lines in the surrounding window. At 10 or more for any of them, that firing was buried, wording was never the binding constraint for it, and the solution should be re-aimed at placement — hold firings to a decision boundary rather than interleaving them with progress.

Committing that bar before looking is the whole point. The number is small and arguable; what is not arguable is that picking it afterwards would let either hypothesis claim the result.

**What a green run here does not settle.** It establishes only that the messages were visible, which is the precondition for wording mattering, not proof that wording is what failed. A firing that was perfectly isolated and still misread could have been misread because the reader did not know what the gate defends, because the criterion was unfamiliar, or because they were tired at the end of a long session. Separating those needs the reader, and none of them is answerable here. This test can kill the content hypothesis; it cannot confirm it.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/telemetry/gate-signal-density.test.ts` — No test files found, exiting with code 1
