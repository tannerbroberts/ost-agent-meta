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

## The full census, by hand, over all 25 shown — unattended sweep, 2026-08-06 (later pass)

The body above says the eyeball estimate — "roughly half are bucket categories" — is "exactly the kind of estimate this assumption exists to replace." This pass replaced it by checking every one of the 25 entries `ost_next_work` returned, one at a time. **This is a hand census, not the instrument's verdict**: the test beneath this assumption is still unrun, no result is recorded, and nothing here promotes this node's rung.

**The count: 23 of 25 are phantom gaps. 1 is a genuine leaf. 1 is retired.**

- **23 phantom** — reported as needing solutions while carrying Solutions in their subtree, because the sweep counts only directly-attached edges. Every one is a category or a parent opportunity whose solution space sits one or more layers below it.
- **1 genuine leaf** — "Waiting on a slow external check burns the session, because every obvious way to wait is refused" was the only entry with no children at all. It did **not** warrant ideation either: it was a flagged duplicate, and this pass folded it into "My loop spends its time waiting for a check it cannot subscribe to", which already carried three solutions covering the space. So the one true gap in the list was an overlap, not a shortfall.
- **1 retired** — "Want proof no hijackable capability even exists", status `deferred`, already carrying 2 solutions.

**Zero of the 25 warranted fresh ideation.** That is the strong form of this assumption, and it is stronger than "most of the list": on this reading the underserved queue currently contains no actionable ideation work whatsoever, and a pass that obeyed it literally would have added 69 solutions on top of an already-served subtree — re-creating precisely the overlap the 2026-08-05 re-parenting removed.

**How each was verified.** Nine were confirmed by reading the node file and inspecting its child-link block directly: "I can't tell what a half-finished run actually finished" (2 Opportunity children), "The same refusal is rediscovered every session" (3), "Improving how the agent works means interrupting it" (2), "The whole loop waits on one human command" (2), "Two agents sharing my vault can trample each other" (2), "What the agent struggles with every session disappears" (3), "The work I most want to run unattended is the work that keeps needing a decision" (3), plus the leaf and the survivor of the merge. For three of those the children were opened as well — "A change I ship can only reach the agent by stopping it first", "A block stops everything and announces itself to no one" and "Two runs write the same vault at once and nothing arbitrates between them" each hold exactly 3 Solutions — so the parents are served two layers down, not merely one. The remaining sixteen were confirmed from the `ost-agent rollup` bucket lines, which are computed from the nodes and report Solutions in each subtree: 6, 6, 6, 6, 9, 10, 11, 18, 23, 25, 31, 34, 45 solutions and so on beneath entries reported as having none.

**Two of the nine carry their own explanation in prose,** which is worth more than the count. "The same refusal is rediscovered every session" says outright: *"This node reads as underserved in `ost_next_work` for that reason — it is a parent opportunity now, not a gap."* "I can't tell what a half-finished run actually finished" carries three 2026-08-05 History lines recording each solution being unlinked and re-parented downward. The nodes knew; the sweep could not see it.

**What this still does not settle.** The quieter failure the body already names is untouched: a parent opportunity carrying a real need distinct from all its children's would be marked served by subtree counting and stop being offered. This census counted subtrees; it did not read the 23 parents to ask whether any holds an unmet need of its own. That question is unanswered, and on this evidence it is now the *more* important one — if subtree counting ships, it silences 23 nodes at once.

_Method: `ost_next_work` for the list, direct reads of the node files for the child-link blocks, and the `ost-agent rollup` supplied to this pass for subtree counts. No test was run. Recorded as corroboration; promotion remains a human's call._

## The quieter failure, measured — unattended sweep, 2026-08-07

The census above closes by naming its own biggest gap: *"a parent opportunity carrying a real need distinct from all its children's would be marked served by subtree counting and stop being offered. This census counted subtrees; it did not read the 23 parents to ask whether any holds an unmet need of its own. That question is unanswered, and on this evidence it is now the more important one."*

This pass read seven of those parents in full and asked exactly that question of each. **Two of seven carry a need their children do not hold. One of the two had no node anywhere in the tree.**

| Parent read | Holds a need its children don't? |
|---|---|
| "Two agents sharing my vault can trample each other" | **Yes** — and it had no node |
| "The whole loop waits on one human command, and nobody is told it is waiting" | **Yes** — ranking which single ask unblocks the most |
| "Improving how the agent works means interrupting it" | Marginal — backing out a change that made things worse |
| "I can't tell what a half-finished run actually finished" | No |
| "The same refusal is rediscovered every session" | No |
| "The work I most want to run unattended is the work that keeps needing a decision" | No |
| "What the agent struggles with every session disappears" | No |

**The first one is the finding.** Since 2026-07-26 that parent has carried, in prose, a distinct failure its two children do not cover: two passes read one briefing, both built the same feature, and roughly eight hours of compute produced a commit that had to be deleted. Its own body says a vault lease would not have helped, because what collided was the decision about what to work on rather than a write. Both children are about writes. The need had lived as a paragraph for twelve days, was never ideated against, and the parent read as fully served — two children, three solutions under each. This pass gave it a node, "A second pass builds what the first already built, because nothing says the work was taken", with three solutions and three instrumented tests beneath it.

**What this does to the solution under this assumption.** It does not argue against subtree counting; the 23-of-25 phantom count stands and the queue is still mostly noise. It argues that the change needs a companion, because shipping it alone would have permanently silenced the node that turned out to be hiding a real gap. Two candidate shapes, neither ideated yet: count the subtree but keep offering a parent whose body has grown since its children were attached, or treat re-parenting as the event that marks a parent served, so a parent that acquired prose *after* its solutions moved down stays visible.

**How weak this measurement is, stated plainly.** Seven of 23, not a sample chosen at random — they are the seven this pass had already opened for other reasons, which biases toward nodes with long bodies, and long bodies are exactly where an unheld need would hide. The true rate across all 23 is likely lower than 2-in-7. It is also a judgement call each time, made by one reader with no second opinion: "does the parent hold a need its children don't" has no exit code. Treat 2 as a floor on the count, not an estimate of the rate.

_Method: direct reads of seven parent node files and their child-link blocks, plus reads of three of the children. No test was run, no result recorded, and this promotes nothing — the instrument beneath this assumption is still unrun._
