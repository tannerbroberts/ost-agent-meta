---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Sweep both vault histories for writes that landed as undefined or empty]]

Putting the guard at the vault rather than the call catches whatever produced the bad content. Whether it is worth having is answered by the histories: a sweep either finds writes that landed as undefined or shows the class is theoretical.
