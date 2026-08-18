---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask the operator whether they'd trust a prior session's task list over reconstructing state themselves]]

A running task list only helps the next pass if reading and trusting it is cheaper than reconstructing state from git/vault history directly, and if the next pass can tell when the list itself is stale (the interrupted session died mid-write, or its plan was already invalidated by what happened after). Otherwise the next pass inherits a wrong plan with more apparent authority than a blank slate would have had.
