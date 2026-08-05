---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Try to confirm a tool surface without invoking any of it]]

The check must run before any work, on every surface the pass runs on. If confirming a tool requires calling it, the check either has side effects or cannot be made — and a single surface where that holds defeats the guarantee.
