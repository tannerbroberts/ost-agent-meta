---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Fewer than 14 of 20 nominations match the assumption the existing test already
  examines.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that nominations are honest — that authors do not simply nominate whatever they were already going to test. If they do, the gate changes nothing except that it has a better name.

**Risk category: feasibility.**

**Design.** Take twenty solutions in the tree that already carry a test. Ask their author, without showing them the existing test, to name the assumption whose falsity would sink each. Then compare: how often does the nomination match what the test actually examines? A high match rate is the failure mode, not the success — it suggests the nomination is a description of existing work rather than an independent judgement.

**Why it is small.** Twenty nominations from material that already exists, and a mechanical comparison.

**What it will not cover.** It cannot say whether nominations are correct, only whether they are independent of what was already done. An author could nominate independently and still nominate badly.

A human runs this and records the result.
