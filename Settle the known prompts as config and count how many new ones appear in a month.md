---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 2 previously unseen prompts stop a run in the month.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the set of prompts is small and stable. It must be maintained — a new tool in the chain brings a new prompt nobody has settled — so the question is the arrival rate.

**Risk category: feasibility.**

**Design.** Settle every prompt observable in the harvested transcripts as committed configuration. Then run normally for a month and count how many previously unseen prompts stop a run. Record each one and whether it had a stable right answer.

**Why it is small.** The initial settling is a handful of config lines, and the measurement is a count of stalls over four weeks.

**What it will not cover.** A month during which the tool chain happens not to change will understate the rate. Noting whether any new tool was introduced during the month is what makes the number readable.
