---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-07'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Two passes reading one briefing would name the same work item the same way]]

**The idea.** Before a pass begins building, it writes a claim naming the work item, the session that took it, and an expiry. The claim is committed where the next pass will look before it chooses — the vault, or a file in the product repo. A pass that finds a live claim on the item it was about to start picks something else or stands down and says why.

**How it differs from its siblings.** This is the only one of the three that prevents the duplicate rather than detecting it or discounting it. It is also the only one that requires the two passes to agree on a vocabulary: a claim only works if both name the same work the same way, which is exactly what the observed collision did *not* have — two readings of one briefing paragraph, converging on the same code without either ever naming it.

**Trade-off, and it is the one that matters.** An expiry that is too short lets a second pass claim work still in progress, which is the failure this is meant to stop. An expiry that is too long strands the item every time a pass dies mid-build, which the tree already records happening — "A run that dies while I am away stays dead, and nothing says where it stopped". So this candidate inherits an unsolved problem: a claim is only as good as the liveness signal behind it, and there isn't one.

**Cost.** Small to write, and the cost is not in the writing. It is in every future pass having to name its work in a shared vocabulary before it may act, which is friction on the path this product most wants to be frictionless.

⚠️ Unvalidated, agent-proposed. Nobody has judged it against the alternatives.
