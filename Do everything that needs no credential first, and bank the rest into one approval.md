---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Classify the steps of ten past runs as credentialed or not, and see how much work sits upstream]]

The run classifies its intended work by whether it needs the operator's secret. It does all the unsecured work first, to completion. Every action that needs the credential is described, queued, and presented at the end as a single list the operator approves or declines in one sitting.

The operator is still in the loop, and deliberately so — this does not try to remove them, only to stop them being the thing a run dies on. A run that ends with twenty finished actions and one pending list is a run that produced value; today it ends at the first locked door with nothing behind it.

**Compared to the alternatives.** By far the cheapest to build: no broker, no token minting, no new trust decision at all. It is also the only one that leaves the operator seeing every credentialed action before it happens, which is exactly what some operators want and will not give up. What it cannot do is unblock work that depends on a credentialed step to continue — those stay queued, and if most of the run is downstream of one push, the reordering buys almost nothing.

**What would make this the wrong pick.** If credentialed steps are load-bearing early rather than terminal, the classification is right and useless. Worth checking against real run journals before building anything.

## Definition of done

[[Classify the steps of ten past runs as credentialed or not, and see how much work sits upstream]]

```
npx vitest run test/loop/credentialed-step-independence.test.ts
```

Red today because no code partitions a run's steps by credential need. The journal records what ran and whether it errored; nothing marks a step as credentialed, and nothing derives which steps sit downstream of one — so there is no fraction to compute. Green means that in at least 6 of 10 recorded runs, half or more of the steps were independent of any credentialed step, asserted over the distribution rather than a mean, because a mean hides the runs where nothing was independent.

That is the number this whole reordering rests on. If most of a run's work sits downstream of one push or one authenticated read, reordering buys nothing and the run still ends with almost nothing accomplished.

What it does not settle: past runs were written by an agent that stopped at the first block, so their step order already reflects that habit. A run designed to defer credentialed work might sequence itself quite differently, and this replay cannot see that counterfactual.
