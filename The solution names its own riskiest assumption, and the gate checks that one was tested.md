---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Authors nominate a riskiest assumption other than the one they were already going to test]]

Every solution carries a nominated riskiest assumption — the single belief whose falsity would sink it — recorded as a field, not as prose. The gate stops counting tests and starts checking whether a test exists against that nomination and has a result. Passing means the thing most likely to be wrong is the thing that was examined.

The nomination is also useful on its own, before any gate consults it. A solution whose author cannot name what would sink it has not been thought about properly, and that is visible immediately.

**Compared to the alternatives.** Mechanically checkable, cheap, and it makes the risk judgement explicit and reviewable rather than leaving it implicit in which test someone happened to write. Its weakness is that the nomination comes from the same author as the solution, so a comfortable nomination produces a comfortable pass — the gate is now enforcing self-assessment rather than counting.

**What would make this the wrong pick.** If authors reliably nominate the assumption they were already going to test, this changes nothing except that the gate has a better name. Whether nominations are honest is the assumption underneath this solution, and it needs testing before the gate is built on it.

## History
- 2026-08-05 unlinked "Have authors nominate a riskiest assumption and check it against what they were already testing" — moved under "Authors nominate a riskiest assumption other than the one they were already going to test" — the belief this test measures now has a node of its own

## Issues
- 2026-11-25 2026-11-24 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. The belief beneath it, "Authors nominate a riskiest assumption other than the one they were already going to test", is about whether a nomination is independent of work already done, and its test, "Have authors nominate a riskiest assumption and check it against what they were already testing", requires an author to nominate blind to the existing test — fewer than 14 of 20 matches is the bar. Every solution in this tree is machine-authored, so compute producing the twenty nominations would be the graded party grading itself; a person is the measurement. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on this surface. Not a skipped step; written so the next firing reads the verdict here instead of re-deriving it.
