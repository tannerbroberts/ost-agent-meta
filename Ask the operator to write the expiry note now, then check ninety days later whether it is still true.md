---
type: AssumptionTest
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
lane: humans-required
threshold: the note is still accurate at 90 days with no more than one edit in between
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.** The cheapest possible version of the candidate is also the test.

**The test.** Ask the operator to write the expiry note today, in one or two sentences, in `ost.config.yaml`. Record the date and the exact text. Ninety days later, show it back to them and ask one question: is this still true, and did you edit it in the meantime?

**Pre-committed threshold:** the note is still accurate at 90 days with no more than one edit in between. More than one edit means it is a recurring-input artifact after all and inherits the staleness failure this project has already recorded elsewhere; inaccurate at 90 days with no edits means it went stale silently, which is the dangerous direction the parent assumption names.

**Why the test is worth running even though it is slow.** It costs the operator two minutes now and one question later, and it is not a simulation — writing the note *is* shipping the candidate in its minimal form. If the note holds, the candidate is already built and the only remaining work is printing it on expiry. If it does not hold, nothing was wasted.

**A second reading worth recording alongside the verdict.** Note whether the operator reached for a durable phrasing ("suite waits belong in the background") or a brittle numeric one ("6-9 minutes"). The parent assumption argues the altitude may matter more than the maintenance discipline, and this test is the only cheap chance to observe which one a person naturally writes.

**What it does not settle.** Nothing about whether a printed sentence actually changes what a session does next — a note can be accurate and still ignored. That is a separate belief and is not carried here.

**Why no instrument.** There is nothing to execute: the question is whether one person's written advice survives ninety days. The feasibility half — whether the config can carry the field at all — was settled by repo sight on 2026-08-29 and is recorded on the parent assumption rather than tested here.

A person outside the building is the measurement here: The operator is the measurement twice over: they write the sentence, and only they can say ninety days later whether it is still true. There is nothing to execute — the whole question is whether one person's one-off written advice survives contact with a changing machine and a growing suite.
