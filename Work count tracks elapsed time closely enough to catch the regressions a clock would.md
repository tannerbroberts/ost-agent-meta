---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Measure whether work count actually tracks elapsed time across vault sizes]]

Counting work removes machine-load flakiness. It only preserves the guarantee if a regression that makes the operation slow also makes it do more countable work — a change that is slower per unit would pass a work-count ceiling untouched.
