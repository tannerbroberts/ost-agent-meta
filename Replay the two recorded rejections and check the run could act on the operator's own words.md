---
type: AssumptionTest
source: 'agent-ideated:2026-08-04-unattended-sweep-question-shape'
created: '2026-08-04'
evidence: assertion
threshold: >-
  Both recorded rejection texts from TRANSCRIPT:42dcb7b4 yield a decision the
  run can proceed on, with no follow-up question emitted.
instrument: npx vitest run test/loop/free-text-answer-parsing.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Feasibility.** The assumption this solution stands or falls on is that a sentence is actionable — that when the operator writes their answer instead of picking it, the run can extract a decision and continue. If it cannot, the open field just relocates the third turn.

This does not need anybody's afternoon. The measurement material already exists: `TRANSCRIPT:42dcb7b4-f01b-40bc-a211-ed4a44a74fd3` recorded two rejections in which the operator wrote what they actually meant. Feed those two texts in as answers and assert the run proceeds without emitting a follow-up question.

**Lane: compute-only.**

**What this does not settle.** Green proves prose can be turned into a decision for these two cases. It says nothing about whether operators would use an open field when a menu is sitting next to it, nor whether the decisions parsed out of prose are the ones the operator meant — the second is a correctness question a passing parse cannot see, and two samples is a fixture, not a rate.
