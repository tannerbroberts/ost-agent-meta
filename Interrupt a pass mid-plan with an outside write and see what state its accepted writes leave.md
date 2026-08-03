---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  In at least 4 of 5, the tree is left coherent and the pass reports its plan as
  compromised.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that refusing the drifted write is enough. An agent that read the tree, formed a plan, and had its premise invalidated will have most of its writes accepted and one refused, leaving a partially-applied plan built on something no longer true — worse than either colliding cleanly or waiting.

**Risk category: feasibility.**

**Design.** Start a pass, let it read and plan, then make an outside write that invalidates part of its premise. Let it continue. Record what it wrote before the refusal, whether the tree is coherent afterwards, and whether the pass noticed that its plan was compromised rather than just that one call failed. Repeat five times with the invalidation at different points.

**Why it is small.** Five runs with one interfering write each, and the vault's history shows exactly what landed.

**What it will not cover.** A deliberately timed invalidation is more adversarial than most real concurrency. The interesting number is how coherent the tree is afterwards, which this measures directly.
