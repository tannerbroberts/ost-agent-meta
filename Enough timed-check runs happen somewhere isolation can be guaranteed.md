---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Count how many timed checks would run somewhere that cannot guarantee isolation]]

Removing the contention instead of tolerating it makes the check meaningful where it can fail. If most runs happen where isolation cannot be promised, the check is advisory almost everywhere — and advisory numbers get scrolled past for months while the regression they watched for arrives.
