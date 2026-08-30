---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
lane: humans-required
threshold: at least 5 of the routed asks answered within 4 weeks
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

**The design.** Route the humans-required solutions into `outstandingAsks` with a start date, tell the operator once that the queue now carries ages, and then leave it alone for four weeks. At the end, count `ost-agent result` filings against entries that arrived by this route. Then — and this is the half that decides the answer — ask the operator about the ones they did not answer: mis-filed, too expensive, or no longer interesting.

**Pre-committed bar, stated before looking:** at least 5 of the routed asks answered within 4 weeks. Below that, the routing candidate is refuted on viability and the sibling that filters silently becomes the default, because it costs one line and asks nobody for anything.

**Why a person and not a spec.** A script can count filings — that part is on disk and cheap. What it cannot supply is why an entry was skipped, and that is the whole question: this vault's 59 standing asks, all with no recorded age, are equally consistent with an operator who does not answer asks and with a queue that never told them anything was waiting. Those two readings recommend opposite decisions, and only the operator can separate them.

**What this does not settle.** Nothing about whether the lane labels on the routed items were correct in the first place — a faithfully answered queue of mislabelled questions is still the wrong queue, and that is the third sibling's subject. It also cannot speak for any operator but this one: a single founder's answering rate is rung `stated` at best and is not demand data.

A person outside the building is the measurement here: Only the operator can say whether an unanswered ask went unanswered because it was mis-filed or because the question is genuinely expensive, and the measurement is their own answering behaviour over four weeks — no artifact on disk carries the reason a question was skipped.
