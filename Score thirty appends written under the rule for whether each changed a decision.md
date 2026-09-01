---
type: AssumptionTest
source: 'agent-ideation:2026-08-31-unattended-sweep'
created: '2026-09-01'
evidence: assertion
lane: humans-required
threshold: no more than 6 of 30 appends are visit-log shaped
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Put the rule in force for two weeks, collect the next thirty appends any pass makes to an existing node, and have a person classify each one.

**Pre-committed bar:** no more than 6 of 30 (20%) are visit-log shaped — recording that a pass occurred, that a prior finding still holds, or that a hold was respected. Above that, the rule is not holding and the candidate beneath it should be retired in favour of a sibling that does not depend on restraint.

**Why this is comparative rather than a verdict on one idea.** The number it produces is what decides between the three candidates under this opportunity, not whether this one "works". A low visit-log rate says restraint is achievable and the cheapest candidate wins. A high one says the write incentive beats the rule, which is an argument for the storage split or the read-path compactor — both of which are indifferent to what a pass chooses to write.

**What a passing result would NOT settle.** Nothing about whether the surviving appends are worth their reading cost, and nothing about the 1,596 node bodies already written — this measures only the flow, never the stock. It also says nothing about the two sibling candidates' own risks, which are routing a reserved section into the unread half, and paraphrase fidelity.

**Baseline available for free:** the 2026-08-31 usage trace records 22 appends against 11 node creations across 21 sessions. Scoring thirty appends from *before* the rule gives a comparison arm at no extra cost, and should be done first — a rule that changes nothing is the most likely outcome and the cheapest to detect.

Unvalidated. Agent-proposed 2026-08-31; a human runs it.

A person outside the building is the measurement here: A person has to read each append and decide whether it recorded a new measurement, a corrected fact or a decision, versus recording that a pass occurred and a prior finding still held. That classification is the whole measurement and no exit code reaches it: the two shapes are identical in structure, length and formatting, and differ only in whether the content was already obtainable elsewhere. The reviewer must also be someone other than the agent that wrote them, since the belief under test is precisely whether the writer's own judgement of "decision-changing" can be trusted.
