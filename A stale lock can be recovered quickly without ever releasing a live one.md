---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Crash a run holding the lock and time how long the vault stays unusable]]

Locks and unattended runs are an uncomfortable pairing. Every recovery policy is either too eager, defeating the lock, or too patient, so a Friday crash costs the weekend — and the unsafe direction, releasing a lock someone still holds, must never happen.
