---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  In at least 4 of 5, the tree is left coherent and the pass reports its plan as
  compromised.
instrument: npx vitest run test/ost/premise-drift-coherence.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that refusing the drifted write is enough. An agent that read the tree, formed a plan, and had its premise invalidated will have most of its writes accepted and one refused, leaving a partially-applied plan built on something no longer true — worse than either colliding cleanly or waiting.

**Risk category: feasibility.**

**Design.** Start a pass, let it read and plan, then make an outside write that invalidates part of its premise. Let it continue. Record what it wrote before the refusal, whether the tree is coherent afterwards, and whether the pass noticed that its plan was compromised rather than just that one call failed. Repeat five times with the invalidation at different points.

**Why it is small.** Five runs with one interfering write each, and the vault's history shows exactly what landed.

**What it will not cover.** A deliberately timed invalidation is more adversarial than most real concurrency. The interesting number is how coherent the tree is afterwards, which this measures directly.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/ost/premise-drift-coherence.test.ts — Runs five passes that read and plan, injects an outside write invalidating part of the premise at a different point in each, and asserts the node's bar: in at least four the tree is left coherent and the pass reports its plan compromised rather than merely reporting one failed call. It fails today because nothing distinguishes a refused write from an invalidated premise, so no pass can report the second.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/premise-drift-coherence.test.ts` — No test files found, exiting with code 1
