---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Every solution carries a nominated riskiest assumption — the single belief whose falsity would sink it — recorded as a field, not as prose. The gate stops counting tests and starts checking whether a test exists against that nomination and has a result. Passing means the thing most likely to be wrong is the thing that was examined.

The nomination is also useful on its own, before any gate consults it. A solution whose author cannot name what would sink it has not been thought about properly, and that is visible immediately.

**Compared to the alternatives.** Mechanically checkable, cheap, and it makes the risk judgement explicit and reviewable rather than leaving it implicit in which test someone happened to write. Its weakness is that the nomination comes from the same author as the solution, so a comfortable nomination produces a comfortable pass — the gate is now enforcing self-assessment rather than counting.

**What would make this the wrong pick.** If authors reliably nominate the assumption they were already going to test, this changes nothing except that the gate has a better name. Whether nominations are honest is the assumption underneath this solution, and it needs testing before the gate is built on it.
