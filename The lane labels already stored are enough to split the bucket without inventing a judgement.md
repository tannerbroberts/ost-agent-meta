---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[The split reports defaulted-parked apart from labelled-parked, rather than folding both into one number]]

**Kind: feasibility, with a usability failure hiding inside it.** The candidate's appeal is that it adjudicates nothing — it just reads the `lane` field already on each test through `computeMayRun` and reports two numbers instead of one. That is only honest if the field actually distinguishes a considered verdict from an unlabelled default.

It probably does not. `src/knowledge/lanes.ts` sends anything unrecognised or missing to `CAUTIOUS_LANE`, which is `humans-required`, and this sweep's own response reports 473 tests in `needsHumans` against 0 `runnable`. Read naively, a two-column report would print "0 actionable, 65 parked" and invite exactly the misreading it was built to prevent — the operator would conclude 65 entries had been judged deliberate when most were never judged at all.

Stated so it could be wrong: a split derived from the stored lane field reports how much has been *decided*, and not merely how much has been *defaulted*.

The likely repair is a third figure — labelled-parked versus defaulted-parked — which is a change to this candidate, not an abandonment of it. That is what makes this the assumption worth testing first: it is cheap, it is answerable from the repository, and the answer changes the design rather than killing it.

**What it leaves untouched.** Whether the operator budgets differently once they see two numbers. That is a fact about a person and no spec reaches it.

## 2026-09-09 — the stored lane field counted, and the actionable column is structurally empty

Kept short, per this branch's convention. Only what is new. This node says its question is "cheap, answerable from the repository, and the answer changes the design rather than killing it". This is that count, taken over the vault rather than the repository, because the field this belief is about is stored on nodes.

**What was counted, first-party this pass.** Over this vault's own node files: **515** `type: AssumptionTest` nodes; **380 of them carry an `instrument:` command** (381 files carry the key in total, one of which the frontmatter window used here did not confirm as a test); **67 carry a `lane:` field**. The two fields are **disjoint** — a two-directional frontmatter search for a file holding both returned zero. So 67 tests carry neither field, and 381 carry a command.

**The finding this belief did not anticipate.** Every one of the 67 lane labels reads `humans-required`. A search for `lane: compute` returns nothing: **the positive label does not occur anywhere in this vault, on any node, once.** So the stored field is not merely sparse, as this node predicted — it is single-valued. A split derived from it cannot place an entry in the actionable column at all, whatever anyone decides, until the first `ost-agent lane --set … compute-only` is issued by hand. The column is empty for a structural reason, not a judgemental one.

**What this does to the belief, stated plainly.** As written — "the stored labels are enough to split the bucket without inventing a judgement" — the census cuts against it for one column and for the other leaves it intact. The parked column is real and 67 entries deep. The actionable column is not a measurement of anything; it is a constant zero. This node's own predicted repair, the third figure separating labelled-parked from defaulted-parked, survives and is more load-bearing than it states: with 448 of 515 unlabelled, defaulted-parked is 87% of the bucket, and a two-column build would report a considered verdict for every one of them.

**The number that most changes how the parent should be read.** `assumptionWork.runnable` is 0, and this pass's summary again reports 0 runnable against 515 needing humans. That is not a statement about instrument coverage, which is 74%: **381 tests carry a runnable command and no lane permits any of them to be run.** The bucket the parent solution proposes to split is therefore not the tree's binding constraint — the tree's binding constraint is that its 381 commands are held by a default nobody has ever overridden. Whoever weighs the parent should weigh it against that, not against the instrument count.

**This is not a result and clears nothing.** No spec was executed, no verdict recorded; this test's own bar is unchanged and its verdict remains a human's `ost-agent result`. It is an observed property of this vault's files — feasibility, never desirability — and it says nothing about whether an operator would budget differently on seeing two numbers, which this node correctly parks as out of reach.

**Limits.** The counts come from frontmatter key searches over `.md` files in this vault, so a node expressing either field another way is missed, and that error runs toward understating both. The disjointness check bounded its search to a 8-line window inside frontmatter and the type-plus-instrument check to 12 lines, so a file with a long multi-line `threshold:` between the keys would fall outside — which is the likeliest reading of the 381-versus-380 gap. `lane: compute` was searched as a prefix, so a differently-spelled permissive value would not have been seen; the four lane names this vault's own tooling reports are the basis for expecting none other. 515 is the rollup's figure and the file count agrees with it. Nothing was executed, no node created, no status changed, no rung moved, no instrument set.

_Method: `Grep` over this vault's own node frontmatter, plus this firing's own `ost_next_work` response. Observed structure of the vault, read first-party._
