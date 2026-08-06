---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Count how many underserved opportunities have a solution somewhere beneath them]]

Feasibility, and it is the load-bearing one: subtree counting is worth building only if the phantom gaps are most of the list rather than a handful.

Stated so it can be false: if the 30 opportunities reported underserved on 2026-08-06 are mostly genuine leaves with no solutions anywhere beneath them, then this change removes a few noisy entries and leaves the real backlog untouched, and the cheaper reading is that the tree simply needs more ideation.

The count that would settle it is mechanical — for each opportunity in `underservedOpportunities`, does its subtree contain a Solution? Eyeballing the 25 shown on 2026-08-06 suggests roughly half are bucket categories carrying large subtrees, but that is an eyeball over a truncated list and is exactly the kind of estimate this assumption exists to replace.

The failure mode on the other side is quieter and is not measured by this test: a parent opportunity that carries a real need of its own, distinct from all of its children's, would be marked served by subtree counting and would stop being offered. Whether any such node exists in this tree is a separate question.

## A within-pass before/after, produced by accident — 2026-08-06 (later pass)

The 2026-08-06 body above says the eyeball estimate is "exactly the kind of estimate this assumption exists to replace." A later pass the same day produced something better than an eyeball without meaning to: a controlled before/after on a single node.

**What happened.** The pass mapped new evidence into a fresh Opportunity, "A run's own leftovers break the next run's setup, so the loop fails before it starts", attached under the bucket "I can't leave the process running unattended without worrying". It then created three Solutions beneath that new opportunity, each with an Assumption and an instrumented AssumptionTest.

**What the sweep said afterwards.** The bucket still reports `solutions: 0, needed: 3`. Three solutions were added to its subtree between two `ost_next_work` calls in one sitting, and its underserved entry did not move by one.

**Why this is stronger evidence than the census it supplements.** The earlier reasoning inferred phantom gaps from node bodies explaining that their solutions had been re-parented downward on 2026-08-05 — good evidence, but historical and reliant on those bodies being accurate. This is a direct manipulation with the sweep read immediately before and after, on a node whose subtree provably gained Solutions during the interval. It rules out the competing explanation that the re-parented nodes were somehow mis-recorded, because these three edges were written by the observing pass itself.

**What it does not do.** It is one node, so it confirms the mechanism counts direct edges and says nothing about the proportion — the threshold on the test beneath this assumption is still what settles whether phantom gaps are most of the list or a handful, and that remains unrun. It also does not touch the quieter failure this assumption's body already names: a parent carrying a real need of its own would be marked served by subtree counting and stop being offered, and nothing here bears on how many such nodes exist.

**One incidental finding from the same interval, recorded where it will be found.** All three new tests carry red-now instruments and all three landed in `assumptionWork.needsHumans`, not `runnable`, because they carry no `lane:` field. Writing an instrument does not make work compute-runnable; only a human's `ost-agent lane --set` does. That is consistent with what the History on "Filter the queue on shipped and count what is still unsatisfiable" already records, and it means the instrumenting effort this loop keeps spending does not, by itself, grow the compute-only lane.
