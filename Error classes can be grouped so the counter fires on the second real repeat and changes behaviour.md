---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Apply the escalating message to the five-failure session and check where it would have fired]]
[[Replay the five-failure and three-failure sessions through the class counter and require it to fire by the second occurrence in both]]

Two zsh failures with different messages are the same class, and two identical messages from different causes are not. Get that wrong and the counter either never fires or cries wolf — and a wolf-crying counter is quickly ignored. Firing is also not enough: the session has to change approach.
