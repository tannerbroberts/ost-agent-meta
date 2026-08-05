---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Set the non-interactive flags and check whether the tools that stalled actually honour them]]

This relies on every invoked tool respecting the declaration, and the ones that ignore it are exactly the ones that caused the problem. A git that prompts despite a non-interactive environment hangs as before — and the run now believes it cannot.
