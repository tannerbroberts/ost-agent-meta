---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A pass that can dismiss its own backlog will not use it to avoid work that mattered]]

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

Zero. Every one of the 23 was *used* — the pass wrote seven substantial corroboration sections from them onto "My loop spends its time waiting for a check it cannot subscribe to", "The same refusal is rediscovered every session, because nothing carries the lesson forward", "I repeat one shell mistake five times in a session, because the first failure never said it was a class", "I probe for files that were never there, because nothing hands me the layout of the workspace I am in", "My unattended run stops at a prompt that assumes a person is sitting there", "Answering one question costs me three turns, because I have to fix its options before I can reply", "The file changed after I read it, and the failed edit is how I find out" and "Two thirds of my calls failed, and each one only told me after I made it" — and not one of them was a case for "I looked at this, and the right action is none".

**So the verb this node proposes would have been used zero times on the largest stranded set this vault has ever held.** The cheaper mechanism the section above floated as a possible narrowing — *let an existing node take an additional `source`* — would have cleared 20 of 23 on its own, and the remaining 3 were cleared years-of-vault-time ago by a written ruling that simply had no way to be recorded in frontmatter.

That is now a measured claim rather than a guess, and it argues for a specific ordering: build the additional-`source` route first, then re-measure how many items are left that no node wants to cite. If the answer stays near zero, this node is a solution to a problem the vault does not have, and the honest end for it is `deferred` with a pointer. This pass is not making that call — it is the party that just spent an hour producing the number, and "Worry the agent is grading its own homework" names exactly why that party should not rule on it.

**One caveat that keeps this node alive.** The classification above is the sweep's own judgement about its own work, and "every item I read turned out to be useful" is precisely the conclusion a pass reaching for justification would reach. "Blind-review a pass's acknowledge-or-map calls on the seven stranded items" is the test that would check it, and it is unrun; it should be re-scoped to twenty-three.

Evidence class: a census of this vault's own state, taken by the pass that hit the wall. Assertion about the artifact, not a measurement of anyone's behaviour.

## Issues
- 2026-08-05 This solution's absence was the binding constraint on the 2026-08-04 unattended pass, and the pass can now say how much it cost. Twenty-four evidence items were read in full. Two revealed needs not already on the tree and became Opportunity nodes. The other twenty-two corroborated needs the tree already holds — the eight-session `sleep`-then-poll refusal, four more stale-Edit failures, eight more blocking clarifying questions, nine more shell-syntax failures, and two usage traces that put a measured number on an existing node's title. That corroboration was recorded, on the five nodes it belongs to, and it made those nodes materially stronger. But there is no way to represent it in the sweep: `ost_next_work` computes "mapped" from node `source:` frontmatter, so an item is cleared only by a node created to cite it. The pass's choices were therefore to duplicate twenty-two needs the tree already has, or to leave twenty-two items outstanding forever. It chose the second. The consequence is that `done` cannot become true on this vault by any amount of correct work, and every future pass will re-read the same twenty-two records to reach the same conclusion — which is itself an instance of the need this node's parent describes. Worth noting for whoever builds this: the acknowledgement wants to record *which existing node* the item was counted toward, not merely that it was dismissed. "Corroborates [[X]]" and "no genuine need" are different verdicts, and only the first should be able to strengthen a node's evidence later. Flagged for human review — the pass cannot build this, and cannot clear the backlog without it.

## Definition of done

"Have a human review a pass's acknowledgements and count how many were avoidance"

`npx vitest run test/ost/acknowledge-evidence.test.ts`

The spec asserts the verb the surface lacks, in the sharpened form the section above argues for rather than the original one: an acknowledged item leaves `unmappedEvidence` without being deleted and without being mapped, its reason persists append-only, and `corroborates [[X]]` is stored as a **distinct verdict** from "no genuine need" — so only the first can strengthen a node's evidence later. Red today because no acknowledge verb exists and mapping is carried solely by node `source:` frontmatter.

**What a green here does not settle, and it is this node's own central worry.** That acknowledgement is indistinguishable from avoidance at the moment it is used. A spec can prove the record is durable, attributed and correctly typed; it cannot tell whether the reason written into it was honest. A pass that can dismiss its own backlog will eventually dismiss something that mattered and will write a reason that sounds entirely reasonable — which is exactly why the humans-required review, and the question of who may acknowledge at all, stay off this instrument.

## The 2026-08-05 sweep hit the same wall, and the number moved slightly

Twenty items, read in full. **Three** revealed needs the tree did not already hold and became Opportunity nodes sourced at the evidence — the cross-session persistence of a correction, tests being instrumented but never run, and a foreign surface's dialect being discoverable only by violating it. The other seventeen corroborate needs already here.

Against the prior passes' 23-items-2-novel and 24-items-2-novel, that is the third consecutive reading of the same shape: **the novel fraction is small, non-zero, and roughly constant.** It is worth recording because it bears directly on the ordering this node's previous section proposed. If the novel rate were zero, the additional-`source` route would be a complete answer. It is not zero — around one item in seven still deserves its own node — so whatever gets built has to leave room for the pass to say "this one is new" as easily as "this one corroborates [[X]]", and must not make the second so much cheaper than the first that a pass stops looking.

This pass also confirmed the mechanism directly rather than by inference: it appended a corroboration section citing an evidence id verbatim, re-ran `ost_next_work`, and the item was still listed as unmapped. Prose citing an id does not map it; only `source:` frontmatter does.

## Census, 2026-08-05 unattended pass

The stranded count is now **18**, up from the seven this solution was written against. Every one of the eighteen was checked by name against the vault this pass, and **all eighteen are already cited in the body of at least one existing Opportunity** — several in three or four:

| Evidence id | Already cited in |
| --- | --- |
| 516fdfb8, 5e5c119d, 92cc492d, 97546e2f, a83f0269, a0eb3fd4 | "I repeat one shell mistake five times in a session…" (22 citations), "I probe for files that were never there…" (12) |
| 87a025f8, 995b8ab1, a0eb3fd4, 516fdfb8 | "My loop spends its time waiting for a check it cannot subscribe to" (20) |
| 2c1b611a, dcdaebdb, 5de6e49b, 748498c4 | "My unattended run stops at a prompt that assumes a person is sitting there" (16) |
| 424486ec, 995b8ab1 | "The file changed after I read it, and the failed edit is how I find out" (11) |
| 748498c4 | "I run git in a folder that was never initialised, and exit 128 is how I learn it" |
| 516fdfb8 | "I compose a hundred and seventy lines before the surface tells me it does not accept that dialect" |
| USAGE:2026-07-25, USAGE:2026-08-03 | "A third of my calls go on re-asking what is outstanding" |
| fd2c6d71 | "The friction that matters leaves no error behind" |

This is the case for this solution stated as a measurement rather than as an argument. The sweep's unmapped test keys on a node's `source:` frontmatter field, and a node carries exactly one. A need with six independent sessions behind it can therefore only ever discharge one of them, and the other five stay on the list forever — not because nobody read them, but because the tree has no way to say "read, filed under an existing need, deliberately not given a node of its own."

The pressure this creates is the thing worth naming: the only way for a pass to clear the counter is to create a near-duplicate Opportunity per stranded item. That is precisely the debt `ost_merge_nodes` exists to pay off, so the sweep is currently rewarding the behaviour the merge tool was built to undo. This pass declined to do it and left all eighteen stranded, which is why the number went up rather than down.

One thing this census does not establish: that every one of the eighteen was *well* filed. It counts citations, not judgement. Whether the filing was accurate is what "Have a human review a pass's acknowledgements and count how many were avoidance" is for, and that remains unrun.

## History
- 2026-08-05 unlinked "Have a human review a pass's acknowledgements and count how many were avoidance" — moved under "A pass that can dismiss its own backlog will not use it to avoid work that mattered" — the belief this test measures now has a node of its own
