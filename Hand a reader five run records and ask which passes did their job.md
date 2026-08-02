---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: usability.** The record is easy to write; the open question is whether writing it changes any conclusion.

**The assumption under test.** That a recorded tool surface actually lets a reader distinguish a real pass from a degraded one. The candidate's own stated weakness is that it prevents nothing and depends entirely on someone reading it. If a reader with the record reaches the same wrong conclusion as a reader without it, the field is decoration.

**The test (five records, two readers, no build).** Take five run records from the 2026-08-01 series — a mix of genuinely degraded passes and the full pass of 2026-08-02 — and produce two versions of each: the record as it exists today, and the same record with a tool-surface block added. Give version A to one reader and version B to another, neither knowing which is which, and ask both the same question: **for each run, did this pass do the work it was scheduled for — yes, no, or cannot tell?**

**Pre-committed threshold.** The reader with the tool-surface block must get **at least 4 of 5 correct**, and must beat the reader without it by **at least 2**. Both conditions, because a small absolute score with a large gap means the record helped and is still not good enough, and a large score with no gap means the existing record was already sufficient and this candidate is unnecessary.

**Why "cannot tell" is an allowed answer and is scored as correct for a degraded run.** The failure being fixed is false confidence, not ignorance. A reader who correctly declines to conclude has not been misled, and treating that as a wrong answer would score the test in the wrong direction.

**Who runs it.** Two humans, half an hour. This is the cheapest test proposed under this branch and does not need the candidate built.
