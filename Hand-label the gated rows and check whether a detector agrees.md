---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
threshold: >-
  A mechanical detector must agree with the hand labelling on at least 26 of the
  32 under-served rows. Agreement below 24 of 32 kills the candidate.
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that the one factor carrying this candidate's real weight — whether a gate, lane or recorded decision holds a row — can be read off the vault mechanically. The other three factors are trivially extractable, so they are not the risk. This one is: every gate in this tree is a paragraph of prose inside a node body, and the candidate's chief stated risk is that a boolean column is too thin a rendering of a paragraph. If a detector cannot even find the gates, the column is noise and the whole table becomes legible-but-wrong, which is worse than absent.

**The test:** hand-label all 32 currently under-served opportunities for whether their own body carries a gate, hold or deferral — reading each node, recording yes/no and the sentence that decides it. Then run a mechanical detector over the same 32 and diff. Both halves read only what is already committed to this vault; no new instrumentation and no operator.

**Pre-committed before running, so this can come out a failure:** the detector must agree with the hand labelling on at least 26 of 32. Between 24 and 25 is a warning that the column ships only with the disagreements listed beside it. Below 24 kills the candidate — at that error rate an operator reading the table would be misled about which rows are actually held, and the tree already records what happens when a counter cannot see a gate.

**Why this one first:** it is the cheapest disconfirmer of the three candidates. It needs no build, no operator and no external party, it runs entirely against committed state, and a refuted result would tell the tree to stop ideating factor-table variants before any of them is built.

**What it deliberately does not cover:** whether the factor values, once correct, change anyone's mind about the order. That is the value question, and this test is deliberately silent on it.
