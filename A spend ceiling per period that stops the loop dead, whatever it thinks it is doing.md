---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The operator sets a budget per day or per week. The loop tracks spend against it and stops when it is exhausted, regardless of how much work it believes remains. The limit is external to the loop's own judgement and cannot be argued with.

This does not try to make the loop honest. It assumes it will not be, and bounds the damage — which is a different and more modest claim than the other two options make.

**Compared to the alternatives.** The only option that works when the loop's own reasoning is the thing that is broken. A stop predicate and a wake signal both rely on the loop correctly evaluating something; a ceiling holds even when it is confidently wrong about how much is left to do. That is also its whole limitation — it caps cost, not waste, and a loop that burns its full budget on invented work will hit the ceiling looking exactly like one that did something useful.

**What would make this the wrong pick.** Used alone it makes the tree's freshness a function of budget rather than of need, and it gives the operator no information about which it was. Best read as a backstop under one of the others rather than as an answer on its own.
