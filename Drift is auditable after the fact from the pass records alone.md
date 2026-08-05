---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Every pass records the outcome text it ran against, and a changed outcome is visible as a change]]

The audit half only works if each pass carries the outcome it ran against, in its own record. If distinguishing two passes requires consulting the vault's current outcome, then the record cannot show what changed — which is precisely the case where it is needed.
