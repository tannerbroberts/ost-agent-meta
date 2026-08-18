---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Zero consumers found reading dist off the shared trunk between firings, or at
  least one named consumer
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: the operator (or someone with the deployment/install path open) confirms whether any consumer installs or loads dist/ straight off the shared trunk rather than from a per-firing branch or its own build step. Threshold: no such consumer, or at least one named.

A person outside the building is the measurement here: Which systems actually install or load from the shared trunk's dist/ is knowledge about deployment, not something this repository alone can answer — the operator or whoever set up the consuming systems has to say.
