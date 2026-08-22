---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  exactly one friction line per completion report, and a run with zero friction
  reports zero rather than omitting the line
instrument: npx vitest run test/friction/completion-report-line.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The question is where a report is assembled and what it contains, which is a fact about committed code.

**Design.** Drive the completion path with a run that recorded friction and one that recorded none. Assert the report carries exactly one friction line in both cases — the zero case matters more than the non-zero one, because a line that appears only when there is something to say is indistinguishable from a line that failed to render, and an operator cannot tell a quiet run from a broken counter.

**Pre-committed threshold:** exactly one friction line per completion report, naming both counts; a run with no friction reports zero rather than omitting the line; and zero additional completion paths emit a report without it.

**What this does not settle.** Feasibility only. Whether an operator notices the line is the sibling assumption, answered by "Ask the operator how often they actually read the run's completion report" and by nothing this command can do. A green here is compatible with the line being read by nobody, which is this candidate's stated weakness.
