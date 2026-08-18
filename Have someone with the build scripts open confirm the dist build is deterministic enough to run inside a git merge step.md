---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  Build script confirmed deterministic and network/environment-independent, or
  confirmed to have a specific non-deterministic step
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: read the build script that produces dist/ for non-deterministic inputs (timestamps, network fetches, environment-dependent output) that would make it unsafe to re-run as a merge driver. Threshold: the build is confirmed reproducible from source alone, or it isn't.

A person outside the building is the measurement here: This pass holds no repo-read grant to inspect the build script for non-determinism. A person with the codebase open (or an attended pass with ost_read_repo) can check this directly against the actual build config.
