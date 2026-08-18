---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Have someone with the build scripts open confirm the dist build is deterministic enough to run inside a git merge step]]

A custom merge driver only resolves the conflict if rebuilding dist/ from each side's source is itself deterministic and side-effect-free at merge time (no missing toolchain, no network fetch, no environment-dependent output). If the build isn't reproducible enough to run inside a git merge step, the driver would itself become a new source of merge failures rather than removing the old one.
