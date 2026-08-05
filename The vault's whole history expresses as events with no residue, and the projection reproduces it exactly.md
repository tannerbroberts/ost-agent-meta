---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Replay this vault's whole git history as events and see if the projection matches]]

Making the log the system of record requires the projection to be lossless. Anything that cannot be expressed as an event, or any node the projection cannot reproduce, means the tree is not actually derived from the log — it is stored twice and one copy is authoritative for reasons nobody has written down.
