---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Most opportunities the sweep calls underserved are categories whose children are already served]]

**The idea.** `underservedOpportunities` counts solutions in an opportunity's whole subtree rather than on its direct edges. An opportunity that has opportunity-children is a category, and a category whose children are well served is not a gap.

**Why.** The tree is explicitly multi-level — the ruleset says opportunities "nest into a multi-level sub-tree" and that "parent-child opportunity relationships represent subsets." Counting only direct solution edges assumes a flat layer that the same ruleset tells the agent not to build. The result is that re-parenting a solution onto the child it actually answers — which is good hygiene, and which the 2026-08-05 pass performed deliberately on three solutions — converts the parent into a permanent phantom gap. The tool punishes the restructuring the rules ask for.

**Sharper form.** Ideating under a parent whose children are served is not merely wasted; it is actively harmful, because the new solutions attach one level too high and address the category rather than the need. The next hygiene pass then has to re-parent them, which recreates the phantom. That is a loop that manufactures its own future work.

**Where it fails.** A parent opportunity can be a genuine gap — it can have children that are all served and still carry a distinct need of its own that nothing addresses. Subtree counting cannot see that case and would silently mark it served. This trades a loud false positive for a quiet false negative, which is the worse direction of the two if the parent needs are the important ones. A reader who wants the old view has no way to ask for it.

**Compared with its siblings.** "Every work bucket excludes nodes whose frontmatter says they are closed" fixes the shipped face and cannot touch this one, because a parent opportunity's status is legitimately `unvalidated`. "A disposition record every bucket consults" would fix this by letting a pass write down "served by children" once — more general, more expensive, and it requires someone to remember to write it, where this derives the answer from edges that already exist.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Count how many underserved opportunities have a solution somewhere beneath them"

```
npx vitest run test/ost/underserved-subtree-count.test.ts
```

Green means the bucket counts Solutions across an opportunity's whole subtree, so a parent whose children are served stops being reported as a gap. The bar is fixed in advance: at least half of the currently-reported underserved opportunities must turn out to have a Solution beneath them, or the phantom-gap theory is refuted and plain ideation is the better answer.

## Census against this node's own bar — 21 of 21 (unattended sweep, 2026-08-09)

**Not a recorded result.** `ost-agent result` is a human's and this pass recorded nothing. This is the count and the method, written so a human can record a verdict in one line if they agree with the reading.

This node's definition of done fixes the bar in advance: *"at least half of the currently-reported underserved opportunities must turn out to have a Solution beneath them, or the phantom-gap theory is refuted and plain ideation is the better answer."*

**Every one of the 21 opportunities `ost_next_work` reported as under-served this pass has at least one Solution beneath it. 21 of 21 — 100% against a 50% bar.**

Not one of them is a flat leaf with no solutions anywhere. Every single one is a grouping node whose direct children are Opportunities rather than Solutions, which is precisely the shape this node predicts the current counter mis-reads.

**The split, since the composition matters more than the total.**

| Group | n | How its subtree was confirmed served |
|---|---|---|
| Direct children of the Outcome (bucket categories) | 15 | `rollup` solution counts per bucket — lowest is 3, highest 48 |
| Intermediate opportunities one level down | 5 | child links read per node, then the child's own solution edges read |
| Retired (`status: deferred`) | 1 | "Want proof no hijackable capability even exists" — carries 2 direct solutions |

The five intermediate ones, with the served child that makes each a category rather than a gap: *Improving how the agent works means interrupting it* → "A change I ship can only reach the agent by stopping it first" (3); *The whole loop waits on one human command, and nobody is told it is waiting* → "A block stops everything and announces itself to no one" (3); *Two agents sharing my vault can trample each other* → "Two runs write the same vault at once and nothing arbitrates between them" (3); *The work I most want to run unattended is the work that keeps needing a decision* → "A run has no authority to decide anything, so every fork is a full stop" (3); *What the agent struggles with every session disappears* → "The same refusal is rediscovered every session, because nothing carries the lesson forward" (3).

**What this adds beyond the theory the node already states.** The body argues from mechanism — that re-parenting a solution onto the child it answers converts the parent into a phantom gap. The mechanism was demonstrated on three nodes the 2026-08-05 pass re-parented. This is the whole population, and it says the false-positive rate of the current counter is not high, it is **total**: on this tree, `underservedOpportunities` currently contains no true positives at all. Every item in it is a category, so a pass that obeys the queue literally would attach 63 solutions one level too high.

**Read the caveat on the denominator.** 15 of the 21 were confirmed from `rollup`'s per-bucket solution counts rather than by opening each bucket and walking its edges. `rollup` computes those counts from the nodes, so this is the tree's own arithmetic rather than an estimate — but it is one channel, not two, and a bucket whose count came from a mis-attributed subtree would be miscounted here the same way. The 6 non-bucket cases were read node by node.

**What it does NOT settle.** Only that the counter's positives are categories. It says nothing about the quiet false negative this node names as its own weakness — a parent that is genuinely a gap in its own right and would be silenced by subtree counting. That risk is untouched by this census and is the assumption "The category exemption does not silence a childless gap" is for. It is also no evidence at all about operators: a count of this vault's own shape, taken by the agent that maintains it.

_Method: the 21 titles returned by `ost_next_work` this pass, checked against `rollup`'s per-bucket figures and against each node's own child links read from the vault. Agent self-observation — it grounds feasibility, not demand. No test was run, no result recorded, and this node's rung is unchanged._
