---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #usability

**Assumption under test (usability, with feasibility riding along):** A human can look at old-process output beside new-process output and tell which is better, quickly and consistently — otherwise the comparison produces cost without a decision.

**Proposed test:** Take one real workflow change, produce three output pairs over the same inputs, and give them to three reviewers independently. Time each judgement.

**Size:** one duplicated pass plus three short reviews.

**Pre-committed threshold:** each pair decided in ≤5 minutes AND ≥2 of 3 reviewers pick the same winner on all three pairs. Split verdicts mean the diff is not legible and the canary is decoration.

**Decides:** whether canarying can gate real workflow changes, or only changes with crisply comparable output.

Proposed by the agent — to be run by human reviewers; the agent must not judge its own output pairs. No results recorded here.
