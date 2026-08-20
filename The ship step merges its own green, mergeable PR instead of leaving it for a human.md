---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The operator will let an unattended firing merge a green PR into main with nobody watching]]

**Variation dimension: who does the work — the loop finishes the job, rather than a human or a later firing.** The window in which a finished build can be re-selected exists because the loop stops one step short: it opens the PR and waits. If the postflight merges a PR that is green on CI, mergeable, and whose instrument has transitioned red→green, the window closes in the same firing that opened it, and there is nothing left for a later firing to rediscover.

**The idea.** `build-pass.sh`'s ship step already refuses a dirty tree and already re-runs the gates ("the suite is the definition of done for everything already shipped"). Extending it to `gh pr merge --squash` when every check it already performs is green is a small mechanical step. The third firing on PR #181 did exactly this by hand — "moved its branch into the main checkout and merged origin/main" — which is both the strongest evidence that the step is missing and the clearest warning: an unsanctioned merge improvised by a model is worse than a sanctioned one performed by the script.

**Against its siblings.** The only candidate that removes the cause rather than detecting its symptom. "Target selection skips…" still spends a `gh` call per firing forever; "A work claim released by the merge" still needs someone to merge. But it is also the only one that widens what an unattended loop may do to the world, and that is a permission no mechanism can grant itself — it belongs beside "Ask the founder whether a machine-cleared permit may start a build with nobody watching", one step further along.

**Where it fails, stated so it can be judged.** A green suite is not a reviewed change; merging on green makes the suite the whole review. Anything the instrument does not cover (the node's own `## Uncovered`, if it has one) ships unread. A flaky CI check becomes a merge-blocker or, worse, a merge-enabler depending on the retry.

**What is deliberately given up.** Human review as a step between build and trunk, for changes whose entire definition was written by a discovery pass.
