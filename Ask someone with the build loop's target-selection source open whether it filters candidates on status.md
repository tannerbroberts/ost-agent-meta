---
type: AssumptionTest
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
lane: humans-required
---
#AssumptionTest #unvalidated #evidence/assertion

Threshold: the answer is a direct yes/no plus the file/line, e.g. "no, the candidate query only checks `hasInstrument` and `permitCleared`" or "yes, it checks `status !== 'deferred'` but the check happens before the human's edit lands." Either answer settles which of the three sibling solutions is worth building.

A person outside the building is the measurement here: Answering this requires reading the build loop's source in the product repository (a separate checkout from this vault); this unattended maintenance pass holds no repo-read grant, so a person with that access must check and report back.
