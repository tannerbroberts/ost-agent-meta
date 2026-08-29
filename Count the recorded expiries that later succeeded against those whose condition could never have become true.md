---
type: AssumptionTest
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
lane: humans-required
threshold: at least 2 of every 3 expiries were genuinely slow rather than never-true
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.** Retrospective and cheap — the corpus already exists.

**The test.** Gather the recorded `await: gave up` events across this vault's captured sessions. For each, determine whether the condition eventually became true (the subject was simply slow) or could never have become true under any budget (wrong path, redirect that never landed, dead subject). Take the ratio.

**Pre-committed threshold:** at least 2 of every 3 expiries were genuinely slow rather than never-true. Below that ratio, automatic escalation makes unattended runs more expensive without making them more likely to succeed, and the parent candidate should be dropped in favour of a sibling that acts on the first expiry rather than indulging the second.

**Why the bar sits at two thirds and not a bare majority.** Escalation is not symmetric in cost: a correct extension buys one success, while an incorrect one burns up to 1800s of additional unattended wall clock before the ceiling stops it. A bare majority would leave the expected cost roughly flat, which is not worth building anything for.

**What a green here would not settle.** It says nothing about the identity problem — whether two distinct waits on one condition string in a session are safely collapsible into one escalating sequence — nor about where the ceiling should sit. Both are named in the parent solution's prose and stay open.

**Why no instrument.** The classification is the judgement, not the parse: a never-true condition and a slow one produce byte-identical expiry lines, so no exit code can separate them. The corpus is the operator's own transcripts. Recorded as humans-required at creation, not left silent.

**Note for whoever runs it.** `TRANSCRIPT:8910f58f` supplies five of the needed events in one place and is the obvious starting point.

A person outside the building is the measurement here: Deciding that a condition could never have become true requires reading the command against what the subject was actually doing — a typo'd path, a redirect that never landed, a job that died early all look identical in the recorded expiry line. That judgement is the measurement, and the sessions holding it are the operator's own transcripts, not anything in this repository.
