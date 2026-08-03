---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check past failures against the snapshot fields before building the snapshot]]

When a step exits non-zero, capture the context that decides whether it can be reproduced — working directory, resolved argv, the tool versions actually on `PATH`, the git SHA and dirty-file count, and the environment variables the step read — and attach it to that record. Successful steps record nothing extra.

**The trade it makes:** cost is paid only where the information is needed, so instrumenting is nearly free on a green run. The price is that a *flaky* step is the hardest case and this handles it worst — you get a snapshot of the failing attempt but nothing to diff it against, because the passing run recorded nothing.

**How it differs from its siblings.** [[Replay a recorded failure in its recorded context on demand]] does not try to record enough to explain a failure; it re-runs it. [[Refuse to record a step whose context could not be determined]] does not enrich the record at all — it declines to produce a misleading one. This is the only sibling that makes the *record itself* self-sufficient, which matters when the machine that failed is not the machine reading the record later.

**Relation to existing work:** [[Every recorded step carries the directory and argv it actually ran with]] sits under a different opportunity and covers the always-on minimum. This is the failure-triggered deep capture; if both existed, that one is the floor and this is the escalation. A human should decide whether they are one solution or two.

Distinguishing assumption: that the context which explains a failure is knowable *at the moment it fails*. Some failures are explained by state that is already gone.
