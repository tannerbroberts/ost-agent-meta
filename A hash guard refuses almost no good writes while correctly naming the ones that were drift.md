---
type: Assumption
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — the belief this solution's test was already
  measuring
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Replay captured sessions to count how often a hash guard would refuse a good write]]

A drift guard is worth having if false refusals are rare — a guard that blocks legitimate writes gets disabled, and then protects nothing. The second half matters as much: it must re-label the recorded failures as drift or not-drift correctly, or it is only changing the error message.
