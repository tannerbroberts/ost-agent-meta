---
type: Solution
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Conditions that expire are more often genuinely slow than never going to be true]]

**Variation dimension: automated-vs-manual. Position taken: the escalation is automated, the ceiling is deliberately manual.**

The wait keeps a small on-disk record keyed by the condition string. The first wait on a condition runs its default budget. A second wait on the *same* condition does not start over: it recognises the key, reports how long it has already spent in total, and doubles its budget — 300s, then 600s, then 1200s — until a total ceiling that a person sets once. When the ceiling is reached the wait refuses to run again and says so, naming the accumulated time.

What stays manual is the ceiling, because it is the only part that encodes a judgement nothing local can make: how much unattended wall clock this operator is willing to spend on one condition before the honest answer is that the approach is wrong.

**Why this shape addresses the observed failure directly.** The 2026-08-29 record on the parent shows five expiries and two byte-identical re-issues. Under this candidate the second call would have said "already spent 300s on this condition, extending to 600s" and the fifth would have refused outright. The information the session lacked — that it was repeating itself and how much it had already burned — is information the waiter already has and currently throws away between invocations.

**Against its siblings.** The heartbeat candidate makes one expiry informative; this one makes a *sequence* of expiries informative and needs no cooperation from the process being waited on, so it works on remote and queued subjects the heartbeat cannot reach. The operator-recorded-instruction candidate is cheaper and asks nobody to build state, but it cannot tell the caller that this is the fourth attempt.

**What would make this the wrong pick.** It rewards patience mechanically, and patience is often the wrong answer: a condition that will never become true gets 2100s of automatic indulgence instead of 300s, which is worse, not better, for an unattended run paying by the minute. It is the right pick only if genuinely-slow subjects are commoner than never-true ones — which nothing here has counted. It also inherits an identity problem: two different waits on the same condition string in the same session are indistinguishable from one wait retried, and collapsing them is sometimes wrong.

**Adjacent node a human should read beside this.** The tree already carries "A budget that is missing, empty or non-numeric makes the wait say so rather than quietly using 300" under a different parent. That is about a budget that never arrives; this is about a budget that arrives, is honoured, and is then discarded between calls. Related mechanism, different failure.

**No instrument.** The helper is on the session's PATH and supplied by the harness, not in this repository, so no spec in this product's `test/` can reach it.

Unvalidated. Agent-ideated on 2026-08-29; a human to review.

## Definition of done — and it is not a command

"Count the recorded expiries that later succeeded against those whose condition could never have become true"

There is deliberately no instrument. The bar is: at least 2 of every 3 expiries were genuinely slow rather than never-true. A never-true condition and a slow one produce byte-identical expiry lines, so no exit code can separate them — the classification is the judgement, and the corpus is the operator's own transcripts.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing:** run the count before building. This candidate is the only one of the three that can make things actively worse if its direction is wrong, and the corpus needed to check the direction already exists.
