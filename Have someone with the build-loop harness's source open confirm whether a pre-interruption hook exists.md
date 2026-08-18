---
type: AssumptionTest
created: '2026-08-18'
evidence: assertion
lane: humans-required
threshold: >-
  A concrete pre-interruption hook is named and confirmed to fire before control
  is lost, or confirmed absent
---
#AssumptionTest #unvalidated #evidence/assertion

Small, fast check: read the scheduling/build-loop harness's own source (outside this vault) for a shutdown/interrupt/backgrounding callback the checkpoint write could hook into. Threshold: a named hook exists and fires before the process loses the ability to write, or it does not.

A person outside the building is the measurement here: This pass holds no repo-read grant, so it cannot open the harness's own source to check for an interruption hook. That is a five-minute code check for a person with the repo open (or an attended pass with ost_read_repo) — not a customer study — but it is currently outside what this unattended surface can verify or fabricate a real instrument for.
