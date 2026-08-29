---
type: AssumptionTest
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
lane: humans-required
threshold: at least 8 of 10 replayed expiries classified correctly by last-line age alone
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Small and retrospective — no new mechanism has to exist to run it.

**The test.** Take ten past sessions in which a wait expired (this vault's friction channel already names several; `TRANSCRIPT:8910f58f` alone carries five). For each, look at what the subject was doing at the moment of expiry and what it did afterwards, and label it *slow-but-finishing* or *genuinely stuck*. Then ask whether the age of the subject's last output line at the moment of expiry would, on its own, have sorted the ten into those two piles.

**Pre-committed threshold:** at least 8 of 10 classified correctly by last-line age alone. Below that, the heartbeat is a number rather than a decision and the parent candidate should be dropped in favour of one of its siblings.

**Why this is worth ten minutes rather than a build.** The parent solution is the most expensive of the three — it needs a change at every call site that starts a long job. This test is a paper exercise over sessions that already happened, and it can kill the candidate before any of that is written.

**What a green here would still not settle.** Nothing about adoption: even if last-line age discriminates perfectly, a job started the ordinary way emits no heartbeat and expires exactly as uninformatively as today. That partial-adoption risk is named in the parent's prose and is a separate belief, untested by this.

**Why no instrument.** The `await` helper is on the session's PATH, supplied by the harness, and the ground-truth labels live in the operator's transcripts — neither is reachable from this product's `test/`, so there is no spec that could go red for this. Recorded as humans-required at creation, not left silent.

A person outside the building is the measurement here: A person has to open the ten sessions in their own transcripts, read past each expiry to see what the subject actually did next, and label each one slow-but-finishing or genuinely stuck. That ground-truth label is the measurement, and nothing in this repository holds it: the outcome lives in the operator's session history, and deciding which of a hung run's symptoms count as "stuck" is a judgement, not a parse.
