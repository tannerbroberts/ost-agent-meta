---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Merge the enabling config into five real project settings files and check nothing was lost]]

Making vault-creation and tool-enablement one event means writing into a file the operator already owns. That is only safe if the merge is non-destructive across the shapes those files actually take in the wild.
