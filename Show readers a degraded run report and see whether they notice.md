---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 4 of 5 readers identify the run as degraded, unprompted, and name at
  least one capability it ran without.
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: usability, with a potential-harm edge.** This is the highest-risk of its three siblings because it is the only one that lets a diminished run finish and report. The danger is not that the fallback does less work — it is that a person reads the report and believes it was a full pass. That is [[A failed pass reports success, so my automation can't tell]] arriving through the front door.

**The test.** Produce two reports from the same vault: one from a full pass, one from a fallback pass with the MCP surface removed. Show five people the degraded one, mixed in among full ones, without telling them what they are looking for. Ask what the run did. Score a pass only if the reader volunteers that it was degraded *and* can say what it skipped — recognising something is off is not enough, because an operator who cannot name the gap cannot decide whether it mattered.

**Why the bar is 4 of 5 and not 3.** The cost of a miss is silent and compounding: an unnoticed degraded run enters the record as a clean one and every later count inherits the error. A candidate that fools one reader in five is already too quiet for an unattended cadence.

**What a failure implies, and it is not "abandon this".** It implies the fallback must be gated behind [[A degraded pass has its own name and is not allowed to report a clean run]] rather than shipped beside it, and probably narrowed to the read-only half named in the solution body — so a degraded run can report but never author.

**Why this one needs people.** The measurement *is* what a human notices. There is no mechanical proxy for it, and constructing one would answer a different question.

Proposed, not run. Recording a result is a human's `ost-agent result`.
