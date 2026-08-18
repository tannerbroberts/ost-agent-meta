---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Ask the operator whether anything reads dist directly off the shared trunk between firings]]

Confining dist commits to per-firing branches only removes the mid-flight conflict if nothing else (a consumer, an install step, a different automation) currently reads dist directly off the shared trunk between firings. If something does, branch-only builds would leave that consumer looking at a stale or missing dist most of the time.
