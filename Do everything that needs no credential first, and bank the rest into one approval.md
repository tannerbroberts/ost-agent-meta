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
