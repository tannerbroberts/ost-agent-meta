---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 2 of 10 runs needed a scope the dispatcher would not have granted.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a run's credentialed needs are predictable before it starts. If runs routinely discover work nobody anticipated, the scopes will be either too narrow to help or wide enough to be the original credential with an expiry date.

**Risk category: feasibility.**

**Design.** Take ten completed runs from the journals and commit history. For each, list the credentialed actions it actually performed, then ask whether a person writing the scope at dispatch time — knowing only the task, not the outcome — would have included every one. Count the runs where at least one action falls outside what would plausibly have been granted.

**Why it is small.** Entirely retrospective, uses records that already exist, and produces one number.

**What it will not cover.** The judgement of what would plausibly have been granted is made by someone who already knows the answer, which biases toward predictability. Splitting that judgement to a second person who sees only the task description would tighten it.
