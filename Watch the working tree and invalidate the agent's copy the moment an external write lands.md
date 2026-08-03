---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Something watches the working tree. When a file the agent has read is modified by anyone else, the agent is told — immediately, in band — that its copy is stale, before it composes anything against it.

**The trade it makes:** it is the only sibling that prevents the wasted work rather than explaining it, and it generalises past editing. Session `424486ec` is the case it is built for: HEAD moved to a merge and roughly fourteen files changed within seconds while the agent was mid-task. A watcher turns that from a forensic discovery into a notification. It also feeds [[Two agents sharing my vault can trample each other]], which needs the same signal for a different purpose.

**The price is the largest of the three.** It needs a live watcher process, it is the most environment-dependent (editors write temp files, formatters touch everything on save, a `git checkout` looks like a thousand external writes), and a noisy watcher is worse than none — an agent told everything is stale will start ignoring the signal. Tuning what counts as a meaningful external write is the whole difficulty, and it is not obviously solvable in general.

**How it differs from its siblings.** Both others act at the moment of the failed write. This one acts at the moment of the change, which is earlier and therefore more valuable and more expensive. It is also the only one that helps when the agent's *reasoning* — not just its edit — was built on the stale copy.

**Cheaper approximation worth costing separately:** poll the mtimes of only the files this session has read, once before each write batch. Most of the benefit, none of the watcher.

Distinguishing assumption: that meaningful external writes are distinguishable from routine churn. If they are not, this degrades into an alarm nobody reads — the failure mode of every watcher ever built.
