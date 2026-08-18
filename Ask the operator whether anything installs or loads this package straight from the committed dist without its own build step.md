---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Zero consumers found expecting a pre-built dist/ with no build step, or at
  least one named consumer
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: the operator confirms whether any installer, plugin loader, or downstream script currently expects dist/ to already exist in a fresh checkout with no build step. Threshold: none found, or at least one named.

A person outside the building is the measurement here: Which systems install or load this package, and how, is knowledge about deployment/distribution that only the operator (or whoever set those consumers up) has.
