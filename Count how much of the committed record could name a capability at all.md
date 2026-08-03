---
type: AssumptionTest
source: 'agent-ideated:2026-08-03-unattended-sweep-builder-capability'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 70 of the last 100 commits and 20 of the last 30 PRs must carry both
  an identifiable author and a body specific enough for a reader to name one
  capability that author exercised. Below 50 of 100 kills the candidate.
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that the committed record is specific enough to support an inference about capability at all. The candidate's whole claim is that it needs no compliance because the artifacts are already there — but "already there" and "legible" are different properties, and if the record is mostly mechanical commits with no attributable reasoning, the profile it produces will be a confident restatement of who touched which file.

**The test:** take the last 100 commits and last 30 PRs in the OST-Agent repo. For each, record two things: whether an author is identifiable, and whether a reader can name one specific capability the author exercised from the artifact alone. Both halves read only what is already committed. No build, no operator, no external party, and no new instrumentation.

**Pre-committed before running, so this can come out a failure:** at least 70 of 100 commits and 20 of 30 PRs must clear both bars. Between 50 and 69 means the profile ships only over the legible subset, with its coverage stated on its face. Below 50 kills the candidate — at that density the archaeology is reading noise, and no amount of later engineering recovers signal that was never written down.

**Why this one first:** it is the cheapest disconfirmer of the three candidates under this opportunity. It is purely retrospective, runs against state already in the repo, and a refuted result tells the tree to stop ideating artifact-archaeology variants before any of them is built.

**What it deliberately does not cover:** whether a profile built from the legible subset would change any routing decision. That is the value question and this test is silent on it. It is also silent on the candidate's stated chief risk — that exercised capability understates real capability — because no reading of the record can detect what the record does not contain.
