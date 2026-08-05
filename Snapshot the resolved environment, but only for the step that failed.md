---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A small fixed set of fields explains most recorded failures]]

When a step exits non-zero, capture the context that decides whether it can be reproduced — working directory, resolved argv, the tool versions actually on `PATH`, the git SHA and dirty-file count, and the environment variables the step read — and attach it to that record. Successful steps record nothing extra.

**The trade it makes:** cost is paid only where the information is needed, so instrumenting is nearly free on a green run. The price is that a *flaky* step is the hardest case and this handles it worst — you get a snapshot of the failing attempt but nothing to diff it against, because the passing run recorded nothing.

**How it differs from its siblings.** "Replay a recorded failure in its recorded context on demand" does not try to record enough to explain a failure; it re-runs it. "Refuse to record a step whose context could not be determined" does not enrich the record at all — it declines to produce a misleading one. This is the only sibling that makes the *record itself* self-sufficient, which matters when the machine that failed is not the machine reading the record later.

**Relation to existing work:** "Every recorded step carries the directory and argv it actually ran with" sits under a different opportunity and covers the always-on minimum. This is the failure-triggered deep capture; if both existed, that one is the floor and this is the escalation. A human should decide whether they are one solution or two.

Distinguishing assumption: that the context which explains a failure is knowable *at the moment it fails*. Some failures are explained by state that is already gone.

## Definition of done

"Check past failures against the snapshot fields before building the snapshot"

```
npx vitest run test/telemetry/failure-context-coverage.test.ts
```

Green means at least 7 of the 10 most recent recorded failures are fully explained by working directory, resolved argv, tool versions and git SHA alone. It is red today because nothing captures those four fields at failure time and no labelled failure set is committed to score against.

**The point of running this before building the snapshot is that it can stop the build.** The assumption is that the context explaining a failure is knowable at the moment it fails; if most failures turn on state that is already gone by the time a recorder runs, the snapshot is expensive decoration. Below 7 of 10 the honest response is to widen the fields or prefer "Replay a recorded failure in its recorded context on demand", which does not have to predict what will matter. Between 7 and 9 argues for shipping this as the floor and escalating to replay for the remainder.

**One caution on the sample.** The founding case for this opportunity — a build step run from the home directory instead of the repo — is explained by `cwd` alone and should be counted, but a result where it is the *only* clean explanation is a result carried by the case that inspired the design.

**What green does NOT settle.** Whether an operator would trust an enriched record enough to stop re-running the failure by hand. That is the desirability question and no coverage count reaches it.

## History
- 2026-08-05 unlinked "Check past failures against the snapshot fields before building the snapshot" — moved under "A small fixed set of fields explains most recorded failures" — the belief this test measures now has a node of its own
