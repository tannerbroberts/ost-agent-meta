---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Add the hook and check whether the commit paths a run actually uses all pass through it]]

A pre-commit hook is a guarantee only if there is no path around it. The node states its own doubt: a local hook is advisory, skippable with a flag, and absent from a fresh clone. If a run's real commit paths bypass it, the marker still reaches the commit.
