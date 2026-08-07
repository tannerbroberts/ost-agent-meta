---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  With `product.repos` unconfigured, an instrument written through the tool is
  recorded `blind` even when the call passes a parameter claiming otherwise;
  with a readable repo configured, the same call records `grounded`.
instrument: npx vitest run test/instruments/sight-provenance.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** The one property that makes the flag worth recording: that the party being graded cannot set its own grade. The second half of the threshold exists so the test cannot be passed by hard-coding `blind`.

**Why it is red today.** `ost_set_instrument` records a command and a reason and nothing about the surface that produced it, so there is no field to assert against.

**Honest limit on the instrument, and it bites hardest here.** This pass had no repo sight, so the spec path is invented and will fail first for absence — the exact defect the parent opportunity describes, occurring inside the test for the fix for that defect. Recorded deliberately.

**What a green here does not settle.** Whether anything downstream reads the flag. A correctly-derived field that no gate and no report consumes leaves the tree in the state the parent complains about, plus a column — and this node's solution names that as its own most likely failure. Confirming a consumer exists is separate work.

There is also a gap the threshold cannot close: a pass with a configured repo but a *denied* filesystem grant would record `grounded` and be just as blind. Both failures were observed on this surface on 2026-08-07 and only one of them is visible at the tool boundary.
