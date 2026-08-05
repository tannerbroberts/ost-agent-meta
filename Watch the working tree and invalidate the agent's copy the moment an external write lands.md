---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Meaningful external writes are separable from churn by a rule fixed in advance]]

Something watches the working tree. When a file the agent has read is modified by anyone else, the agent is told — immediately, in band — that its copy is stale, before it composes anything against it.

**The trade it makes:** it is the only sibling that prevents the wasted work rather than explaining it, and it generalises past editing. Session `424486ec` is the case it is built for: HEAD moved to a merge and roughly fourteen files changed within seconds while the agent was mid-task. A watcher turns that from a forensic discovery into a notification. It also feeds "Two agents sharing my vault can trample each other", which needs the same signal for a different purpose.

**The price is the largest of the three.** It needs a live watcher process, it is the most environment-dependent (editors write temp files, formatters touch everything on save, a `git checkout` looks like a thousand external writes), and a noisy watcher is worse than none — an agent told everything is stale will start ignoring the signal. Tuning what counts as a meaningful external write is the whole difficulty, and it is not obviously solvable in general.

**How it differs from its siblings.** Both others act at the moment of the failed write. This one acts at the moment of the change, which is earlier and therefore more valuable and more expensive. It is also the only one that helps when the agent's *reasoning* — not just its edit — was built on the stale copy.

**Cheaper approximation worth costing separately:** poll the mtimes of only the files this session has read, once before each write batch. Most of the benefit, none of the watcher.

Distinguishing assumption: that meaningful external writes are distinguishable from routine churn. If they are not, this degrades into an alarm nobody reads — the failure mode of every watcher ever built.

## Definition of done

"Classify every filesystem event in three real sessions as meaningful or churn"

```
npx vitest run test/runner/fs-event-classification.test.ts
```

Green means a rule fixed in advance classifies at least 90% of external write events correctly against a committed hand-labelled ground truth, and produces no more than 3 unnecessary invalidations per session. It is red today because no classification rule exists and no event capture is committed to score against.

**The second clause is the binding one and the first is the one that sounds impressive.** A 90% classification rate can still mean several spurious invalidations an hour, which is enough for an agent to start ignoring the signal — the failure mode of every watcher ever built. Three per session is the number that decides whether the mechanism survives contact with use, and a command asserting only the rate would go green on a watcher already on its way to being background noise.

**Writing the rule before looking at the data is part of the test, not hygiene.** Editors write temp files, formatters touch everything on save, and a `git checkout` looks like a thousand external writes at once. A rule tuned against the very sessions it is scored on measures nothing except that it was tuned.

**What a red result redirects to, and it is a real fallback rather than a consolation.** Poll the mtimes of only the files this session has actually read, once before each write batch. That sidesteps classification entirely by only asking about files it already cares about, and if this test fails it becomes the stronger candidate.

**A by-product worth keeping.** The same event capture would show how often two writers genuinely overlap — direct evidence for "Two agents sharing my vault can trample each other", a node currently resting on two anecdotes.

## History
- 2026-08-05 unlinked "Classify every filesystem event in three real sessions as meaningful or churn" — moved under "Meaningful external writes are separable from churn by a rule fixed in advance" — the belief this test measures now has a node of its own
