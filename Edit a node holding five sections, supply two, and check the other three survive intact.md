---
type: AssumptionTest
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  All three unsupplied sections present and byte-identical after the edit; the
  two supplied sections replaced; no section duplicated; total section count
  unchanged at five.
instrument: npx vitest run test/mcp/edit-node-preserves-unsupplied-sections.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Replacement node — full prose arrives with the merge that folds in the mis-cited original.
