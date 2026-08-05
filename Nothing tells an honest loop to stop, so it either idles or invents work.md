---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-passes-8-through-13-produced-zero-structure-whil.md'
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Publish a stop condition the loop can evaluate, and make idling the honest default]]
[[The loop sleeps on a signal and is woken by the event, instead of deciding when to look]]
[[A spend ceiling per period that stops the loop dead, whatever it thinks it is doing]]

Six consecutive passes produced no structure at all while the outstanding-work report named the same items every time. The loop had nothing it could honestly do — the unmapped count was inflated by items already dispositioned in a ledger the counter could not read, and every underserved opportunity was gated — but nothing in the loop said so.

The failure mode splits by temperament rather than by capability. A governed agent idles and burns passes discovering the same standstill; an ungoverned one fills the quota with invented structure. Both are paid for identically, and only one of them is visible afterwards. The honest move at pass thirteen was to file a friction note and do nothing, which is exactly the move no part of the system asks for.

**The need:** when there is genuinely nothing to do, I want to be told that, rather than pay for passes that rediscover it.

More than one way to address this: distinguish "blocked" from "outstanding" in the report, emit an explicit idle-down signal the scheduler can read, decay the pass frequency when consecutive passes commit nothing, or require a pass that commits nothing to say why in one line.

## Provenance

Distilled from `INBOX:2026-07-25-friction-passes-8-through-13-produced-zero-structure-whil.md` — filed by the twenty-passes ambient driver, observing the idle-down problem from inside it.

## History
- 2026-08-02 evidence: stated → assertion — Demoted from 'stated' for consistency: rests on an inbox friction note, and the inbox channel's earned ceiling is 'assertion'.

## The sweep asked for 75 solutions that would have undone the previous pass — 2026-08-05

`ost_next_work` reported 25 opportunities with fewer than three solutions and asked this pass to ideate up to the minimum. Ideating all of them would have created 75 Solution nodes, plus an Assumption and an AssumptionTest beneath each to satisfy the next bucket — roughly 225 nodes onto a tree of 920, in one firing.

**Every one of the 25 is a category node, and its solutions were moved off it deliberately the day before.** Eight were checked by reading the file rather than inferring: *Two agents sharing my vault can trample each other*, *I can't tell what a half-finished run actually finished*, *The whole loop waits on one human command, and nobody is told it is waiting*, *The same refusal is rediscovered every session*, *What the agent struggles with every session disappears*, *Improving how the agent works means interrupting it*, *The work I most want to run unattended is the work that keeps needing a decision*, and *The same agent has a different tool surface on every surface I run it on*. Each has only Opportunity children, and each carries History lines dated 2026-08-05 of the form:

> unlinked [[…]] — re-parented under [[…]] — this solution answers that need, not the categories beside it

The remaining seventeen appear in `ost-agent rollup` as buckets with populated subtrees — *Trust an unmonitored agent enough to walk away* alone reports 10 opportunities, 28 solutions and 29 tests beneath it, while the sweep calls it a node with zero solutions.

**The defect.** The under-served rule counts a node's *direct* Solution children and is blind to whether that node is a leaf need or a category parenting other needs. The tree's shape rule (`outcome-files-categories`) requires exactly this two-level opportunity structure, so the healthier the bucket layer gets, the more work the sweep invents: every re-parenting that correctly moves a solution down onto the need it answers empties a category node and books three fresh solutions against it.

**Why this is this node's evidence.** The claim here is that a loop with no honest stopping condition either idles or invents work. This is the second mode, arriving through a counter rather than through boredom, and it is self-reinforcing — a pass that complies produces exactly the mis-parented solutions the previous pass spent its firing removing, and next hour's pass gets to move them down again. Two passes could run this cycle indefinitely, each doing defensible work, with the tree growing and nothing being learned.

**This pass did not ideate under any of the 25**, and that is a refusal to be reviewed rather than a step skipped.

**For a human — the candidate fix, stated so it can be argued with.** Exclude from the under-served count any Opportunity that has Opportunity children, or count a category node's solutions transitively over its subtree. Under either rule all 25 drop out, and the bucket becomes a claim about leaf needs, which is the only place a solution belongs anyway. Whether a category node should ever carry a cross-cutting solution of its own is the question that decides between the two, and it is a design call, not a sweep's.

_Observed by the 2026-08-05 unattended sweep, from the tool's own output and the vault's own History lines. Grounds usability, not demand._
