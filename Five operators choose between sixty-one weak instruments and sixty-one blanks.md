---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
lane: humans-required
threshold: >-
  At least 4 of 5 operators, shown both artefacts without being told which the
  product prefers, choose the blank-and-lane outcome. 3 or fewer refutes the
  gate and argues for the marking sibling instead.
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether the throughput-for-groundedness trade this candidate makes is one an operator would accept. Both artefacts are shown as artefacts — a real page of sixty-one instruments naming files that do not exist, and a real page of sixty-one solutions with no instrument and a named lane — with no framing about which is correct.

**Why no instrument.** There is no code fact here. The parent assumption is about what someone prefers, and the repository cannot hold a preference. This is a legitimate human-required test, not a command nobody wrote.

**How to avoid the obvious way to get a useless answer.** Asked abstractly, everyone says they want groundedness. The artefacts have to be shown, and the follow-up question has to be what they would do on Monday with each — because the answer that matters is behavioural, and the stated one will be flattering.

**What a result here does not settle.** Anything about the other two candidates in this branch. It compares this gate against doing nothing; if it refutes, "An instrument records whether the pass that wrote it could see the repository" is still standing and is untouched by this finding.

A person outside the building is the measurement here: Five people who run an unattended agent overnight and pay for the compute. The measurement is their preference between two artefacts, which nothing in the repository can supply — and the party proposing the gate is the party that would be gated, so an internal judgement here is worth nothing.
