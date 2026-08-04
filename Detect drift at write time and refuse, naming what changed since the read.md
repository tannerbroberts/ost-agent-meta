---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Interrupt a pass mid-plan with an outside write and see what state its accepted writes leave]]

No coordination up front. Every write carries a fingerprint of the state it was composed against, and the write is refused if that state has changed. The refusal names what moved and who moved it. Agents proceed optimistically and are stopped only where they would actually collide.

This suits an append-only vault well, because the genuine collisions are rare and narrow — two appends to different nodes are not a collision at all, however concurrent they are.

**Compared to the alternatives.** Costs nothing when there is no contention, which is nearly always, and it never serialises work that did not need serialising. It also never prevents the wasted effort: an agent that composed a whole pass against stale state finds out at the end, and has to redo it. A lock would have made it wait first; branches would have let it finish and merge.

**What would make this the wrong pick.** Detection catches the write and not the reasoning. An agent that read the tree, formed a plan, and had its premise invalidated will have most of its writes accepted and one refused, leaving a partially-applied plan built on something no longer true — which is a worse state than either colliding cleanly or waiting.

## Definition of done

[[Interrupt a pass mid-plan with an outside write and see what state its accepted writes leave]]

```
npx vitest run test/ost/premise-drift-coherence.test.ts
```

Green means that across five passes interrupted at five different points, at least four left the tree coherent **and** reported their plan as compromised rather than merely reporting one failed call. It is red today because nothing distinguishes a refused write from an invalidated premise, so no pass is able to report the second thing.

**The second clause is the one that matters, and it is the one this solution is most likely to fail.** Refusing the drifted write is the easy half and this node already argues for it. The risk the test targets is what the refusal leaves behind: a pass that read the tree, formed a plan, had most of its writes accepted and one refused, and carried on — leaving a partially-applied plan resting on a premise that is no longer true. That is worse than colliding cleanly and worse than waiting, because it looks finished. A spec asserting only that the drifted write is refused would go green on exactly that outcome.

**What green does NOT settle.** A deliberately timed invalidation is more adversarial than most real concurrency, so the command establishes behaviour under a hostile schedule rather than a frequency under a realistic one. It also says nothing about the operator-facing question — whether a person reading "your plan was compromised" can act on it — which is [[Two agents sharing my vault can trample each other]] territory and needs a reader, not an exit code.
