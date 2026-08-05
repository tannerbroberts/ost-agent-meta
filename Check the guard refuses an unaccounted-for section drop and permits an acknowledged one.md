---
type: AssumptionTest
source: 'first-party-observation:2026-08-05 unattended pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Both directions must hold. Refuses when a stored section appears in neither
  `prose` nor `dropping:`, and the refusal message names the section by heading.
  Permits when the section appears in either. A guard that satisfies only one
  direction fails.
instrument: npx vitest run test/mcp/edit-node-unacknowledged-section-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Replacement node — full prose arrives with the merge that folds in the mis-cited original.
