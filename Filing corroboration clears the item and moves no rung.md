---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  After filing thirty items as corroboration of one opportunity: the items are
  absent from `unmappedEvidence`, the node's corroboration count is 30, no node
  was created, and the node's `evidence` rung is byte-identical to what it was
  before.
instrument: npx vitest run test/evidence/corroborate-disposition.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** That corroboration is the light act it claims to be. Thirty is chosen because it is roughly the scale a single pass would file from this corpus, and because the rung assertion is the one that matters: thirty recordings of one channel are one channel observed thirty times, and the ladder must not read that as thirty sources.

**Why it is red today.** There is no corroboration disposition. The only way to discharge an evidence item is to create a node citing it, so every assertion in this file fails.

**Honest limit on the instrument.** This pass could not read the product repository, so the spec path is invented and will first fail because it is absent rather than because the evidence store disagrees. Recorded rather than hidden; see "My instruments are red because a file is absent, not because the behaviour is".

**What a green here does not settle.** Whether the judgement "this confirms an existing need" is being made correctly. This file pins the mechanics of a filing and is completely blind to whether the filing was right — including the novelty-hiding failure the parent opportunity names as the main risk. That question needs a reader, not a spec.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/evidence/corroborate-disposition.test.ts` — No test files found, exiting with code 1
