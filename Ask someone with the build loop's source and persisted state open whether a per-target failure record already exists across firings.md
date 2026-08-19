---
type: AssumptionTest
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
lane: humans-required
---
#AssumptionTest #unvalidated #evidence/assertion

Threshold: the answer names whether any file or record already tracks "target X failed its instrument on firing Y" across runs, and if so why it did not prevent the three re-selections observed on 2026-08-16 and 2026-08-19.

A person outside the building is the measurement here: Answering this requires reading the build loop's source and its persisted state directory (e.g. `.local/state/ost-build-loop/`) in the product repository; this unattended maintenance pass holds no repo-read grant, so a person with that access must check and report back.
