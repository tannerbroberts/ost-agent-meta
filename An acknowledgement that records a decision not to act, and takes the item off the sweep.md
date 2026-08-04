---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Have a human review a pass's acknowledgements and count how many were avoidance]]

Give a pass a way to say "I looked at this, and the right action is none" — recorded, with a reason, append-only, and honoured by the sweep. The item leaves the outstanding list without being deleted, without being mapped, and without anyone pretending it was work.

This is the verb the current surface lacks, and its absence has a measurable cost. On 2026-08-03 this vault held eighteen evidence items that could not be mapped without either inventing a customer need or duplicating an existing one, both refused. They will be reported as outstanding on every pass forever. A loop under standing pressure to reach `done` against an unreachable list is a loop being taught to manufacture work — which is exactly the failure a sibling opportunity in this tree already names.

**Compared to the alternatives.** The only option that actually resolves an item nobody may act on, and the record it leaves is more useful than silence: eighteen acknowledgements with reasons is a specification for whatever schema gap caused them. It also introduces the most dangerous verb on the surface, because acknowledgement is indistinguishable from avoidance at the moment it is used.

**What would make this the wrong pick.** A pass that can dismiss its own backlog will eventually dismiss something that mattered, and the reason it writes will sound entirely reasonable. Who may acknowledge, and whether an acknowledgement expires, are human decisions — and this pass is precisely the wrong party to be trusted with them.

## A worked instance from the 2026-08-04 sweep

This solution's case can now be stated with numbers rather than in the abstract. An unattended pass read all 23 unmapped evidence items in full and could clear only 2 of them. The other 21 are still on the sweep, and will be on the next one, and every pass from here pays to re-read them.

**They are not unmappable. They are already mapped, and the vault has no way to say so.** Nine sessions show the same blocked `sleep`-then-poll; six show the run stopping to ask a design question it had a Recommended answer for; six show a path guessed at and discovered wrong by failing. Each of those needs is already an opportunity in this tree, some of them for months. The pass wrote the corroboration onto those nodes — session ids, counts, what the repetition adds that a single capture did not — which is real work and made the nodes better. It changed nothing about the sweep, because mapping is carried by a node's `source` frontmatter and only `ost_create_node` writes one.

So the surface offers exactly two moves for an item that corroborates an existing node: create a duplicate opportunity to hold the `source`, or leave it outstanding forever. The first is worse. Twenty-one near-duplicate opportunities would each draw three solutions and three tests behind them, and the tree would grow by roughly 150 nodes restating needs it already holds — which is the debt this vault has spent several passes paying down.

**What this instance sharpens about the design.** The obvious framing of this solution is "a way to dismiss an item nobody will act on", and dismissal is the wrong verb for most of what is stranded here. These items were *read, understood, and used*; what they were not is novel. A single acknowledgement that means both "not worth acting on" and "already known, filed against an existing node" would erase the difference between an item the tree learned from and one it discarded — and the second reading is the one a later reader most needs, because a need corroborated by nine independent sessions is a different claim from one asserted once.

The cheaper mechanism this suggests, worth weighing against the acknowledgement as designed: let an existing node take an additional `source`. Then corroboration maps the item by the same rule that already governs mapping, no new verb is needed, and the count of sources per node — which the rollup already reports — starts meaning something. That does not cover items with genuinely no need in them, so it does not replace this solution; it may shrink it to the case it was actually for.

Evidence class: a census of this vault's own state, taken by the pass that hit the wall. Assertion about the artifact, not a measurement of anyone's behaviour.

## A second pass hit the same wall the same day — and it shrinks this solution rather than strengthening it

The section above was written by the 2026-08-04 sweep, which read 23 items, cleared 2, and left 21. A later unattended pass on 2026-08-04 ingested 2 new transcript records, bringing the list back to **23**. Two cleared, two arrived, net zero.

**That is the first datum here about rate rather than size.** The stranded set is not a backlog draining slowly; it is at steady state, because the channels that produce it (`transcript`, `usage`) run continuously and the clearing rate is bounded by how many items happen to contain a genuinely novel need. A backlog that stays the same size across two passes on one day will stay the same size indefinitely, and every pass from here pays the full re-read cost of all 23 to discover that.

**The finding that bears on the design, and it cuts against this node.** The later pass classified all 23 by what disposition each actually needs:

| Disposition the item needs | Count |
| --- | --- |
| Corroborates an opportunity already in the tree | 20 |
| Already dispositioned by a prior explicit ruling (`USAGE:` clean days, "a clean day reveals no need of its own") | 3 |
| Genuinely reveals no need and nobody should act on it | **0** |

Zero. Every one of the 23 was *used* — the pass wrote seven substantial corroboration sections from them onto [[My loop spends its time waiting for a check it cannot subscribe to]], [[The same refusal is rediscovered every session, because nothing carries the lesson forward]], [[I repeat one shell mistake five times in a session, because the first failure never said it was a class]], [[I probe for files that were never there, because nothing hands me the layout of the workspace I am in]], [[My unattended run stops at a prompt that assumes a person is sitting there]], [[Answering one question costs me three turns, because I have to fix its options before I can reply]], [[The file changed after I read it, and the failed edit is how I find out]] and [[Two thirds of my calls failed, and each one only told me after I made it]] — and not one of them was a case for "I looked at this, and the right action is none".

**So the verb this node proposes would have been used zero times on the largest stranded set this vault has ever held.** The cheaper mechanism the section above floated as a possible narrowing — *let an existing node take an additional `source`* — would have cleared 20 of 23 on its own, and the remaining 3 were cleared years-of-vault-time ago by a written ruling that simply had no way to be recorded in frontmatter.

That is now a measured claim rather than a guess, and it argues for a specific ordering: build the additional-`source` route first, then re-measure how many items are left that no node wants to cite. If the answer stays near zero, this node is a solution to a problem the vault does not have, and the honest end for it is `deferred` with a pointer. This pass is not making that call — it is the party that just spent an hour producing the number, and [[Worry the agent is grading its own homework]] names exactly why that party should not rule on it.

**One caveat that keeps this node alive.** The classification above is the sweep's own judgement about its own work, and "every item I read turned out to be useful" is precisely the conclusion a pass reaching for justification would reach. [[Blind-review a pass's acknowledge-or-map calls on the seven stranded items]] is the test that would check it, and it is unrun; it should be re-scoped to twenty-three.

Evidence class: a census of this vault's own state, taken by the pass that hit the wall. Assertion about the artifact, not a measurement of anyone's behaviour.
