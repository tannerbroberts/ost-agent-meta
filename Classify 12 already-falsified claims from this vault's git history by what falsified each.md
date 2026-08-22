---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
lane: humans-required
threshold: >-
  Of 12 claims found already falsified in this vault's history, at least 7 must
  have been falsified by a record the vault later ingested. 6 or fewer refutes
  the assumption and closes the ingest-time candidate.
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold, fixed before anybody looks:** walk this vault's git history and this tree's dated sections for **12 claims that are now known to have been false at some point after they were written**. For each, name what falsified it, and sort into three: **(a)** a record the vault later ingested, **(b)** a change the vault never ingested — config edited by hand, code shipped, a grant table changed elsewhere, **(c)** wrong when written, with no falsifying event at all. **At least 7 of 12 must land in (a).** At 6 or fewer the assumption is refuted and the ingest-time candidate is closed, not narrowed — the sibling feasibility test may still come back green and that would not save it.

Class (c) is counted and reported separately even though it argues against every candidate under this node, because it is the one outcome that says the need itself is mis-framed: a claim that was never true did not go stale, and no re-measurement schedule reaches it.

**One instance is already in hand and it is class (a):** the 2026-08-16 census on "The unattended run is scoped for tools nobody granted it, and it finds out one denial at a time", falsified by `TRANSCRIPT:90d8aeae-192e-4adf-9dd5-746832e3753e` the following day. It counts as one of the 12 and is stated here so the sample is not quietly seeded with the case that motivated the question — the other 11 must be found without knowing the answer.

**Why a person and not a command.** Deciding that a claim went stale is a reading of what it asserted; deciding what falsified it is a reading of causation. Neither is a pattern. And an agent auditing whether its own past passes wrote claims that decayed is the self-grading failure this tree's mandate exists to catch, which is a second and independent reason this one is not compute's to run.

**What this does not settle even at 12 of 12.** Nothing about whether the check is buildable — that is the sibling assumption's test beneath the same solution — and nothing about the other two candidates under this opportunity, both of which are indifferent to what caused a claim to decay.

A person outside the building is the measurement here: A person has to decide, per claim, both that it went stale and what falsified it — a judgement about meaning that no pattern holds, and one an agent grading its own tree should not make about its own past passes. Reading git history mechanically finds edits, not claims that quietly stopped being true while nobody edited them, which is the entire population of interest.
