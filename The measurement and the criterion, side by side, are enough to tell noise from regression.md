---
type: Assumption
status: unvalidated
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Feasibility, and the one this solution lives or dies on.** Putting the two numbers together assumes their difference carries the answer. It very likely does not.

A run that took 340ms against a criterion of 200ms looks identical whether the machine was sharing a core with a build or the code got slower. The pair is the same pair. Nothing in "measured 340, criterion 200" distinguishes the two causes, which means this solution as titled could be built exactly as described, render both numbers perfectly, and leave the operator with precisely the question they started with — which is the parent opportunity's complaint verbatim.

Stated so it can be false: the difference between a measurement and its criterion is sufficient to classify the failure. False whenever the machine's own variance is comparable to the margin, which on a laptop running a test suite and a browser is most of the time.

What would make it true is a third number the title does not mention: the spread. If the gate also carries what the same commit measures across repeated runs, then 340 against a criterion of 200 with a same-commit band of 180–210 is a regression, and the same 340 with a band of 150–400 is noise and the criterion was never measurable on this machine. That is a different rendering and arguably a different solution, and if the test below fails, the honest response is to rewrite this node rather than to keep it and add a fourth number.

There is a cheaper failure mode underneath. If no same-commit repeats are recorded anywhere, the band cannot be computed at all, and the gate has no way to know its own variance. In that case this is not a rendering problem, it is a missing-observation problem, and the work is upstream of anything the gate can display.
