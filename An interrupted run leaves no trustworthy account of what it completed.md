---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Every recorded step carries the directory and argv it actually ran with]]
[[A run journal written as it goes, so an interrupted run reads as a list of finished steps]]
[[Reconstruct what finished from the commit history, so no run has to be trusted to report]]

The run's own report is written at the end, so a run that does not reach the end reports nothing. What it did finish has to be inferred from side effects, and the inference is unreliable precisely when it matters most — after a failure.
