---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[One writer at a time, enforced by a lock the second agent waits on rather than ignores]]
[[Each agent writes on its own branch, and merging is a deliberate, reviewable step]]
[[Detect drift at write time and refuse, naming what changed since the read]]

There is no lock, no branch, and no drift check. Two agents reading the same state and writing back their own version of it is an ordinary occurrence rather than an edge case, and the loser's work disappears without either run noticing.
