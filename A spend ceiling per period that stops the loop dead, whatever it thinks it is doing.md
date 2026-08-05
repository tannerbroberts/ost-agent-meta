---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Spending more does not buy proportionally more worth having, so a hard stop costs little]]

The operator sets a budget per day or per week. The loop tracks spend against it and stops when it is exhausted, regardless of how much work it believes remains. The limit is external to the loop's own judgement and cannot be argued with.

This does not try to make the loop honest. It assumes it will not be, and bounds the damage — which is a different and more modest claim than the other two options make.

**Compared to the alternatives.** The only option that works when the loop's own reasoning is the thing that is broken. A stop predicate and a wake signal both rely on the loop correctly evaluating something; a ceiling holds even when it is confidently wrong about how much is left to do. That is also its whole limitation — it caps cost, not waste, and a loop that burns its full budget on invented work will hit the ceiling looking exactly like one that did something useful.

**What would make this the wrong pick.** Used alone it makes the tree's freshness a function of budget rather than of need, and it gives the operator no information about which it was. Best read as a backstop under one of the others rather than as an answer on its own.

## Definition of done

[[Read back four weeks of spend and judge how much bought something worth having]]

`npx vitest run test/loop/spend-ceiling.test.ts`

The spec asserts what this node claims is its whole advantage — that the limit is external to the loop's own judgement. It drives the loop to the ceiling with a stop predicate that insists work remains, and requires the loop to halt anyway. It is red today because no per-period spend accounting or ceiling exists.

**What a green here does not settle.** It shows the ceiling holds when the loop's reasoning is the broken thing, which is exactly the case the node was written for. It cannot tell anyone whether the spend bought anything — the node says so itself: this caps cost, not waste, and a loop that burns its budget on invented work hits the ceiling looking identical to one that did something useful. Judging which happened is the humans-required test and no spec substitutes for it.

## History
- 2026-08-05 unlinked [[Read back four weeks of spend and judge how much bought something worth having]] — moved under [[Spending more does not buy proportionally more worth having, so a hard stop costs little]] — the belief this test measures now has a node of its own
