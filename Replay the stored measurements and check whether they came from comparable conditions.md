---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Provenance is recoverable for at least 80% of measurements, and within-machine
  spread is under half the across-machine spread.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the history is comparable — same machine, similar conditions. If the stored measurements are a mix of laptop and CI runner, idle and loaded, the distribution is noise with a confidence interval drawn around it, and the gate will be quietest exactly when the data is worst.

**Risk category: feasibility.**

**Design.** Take whatever timing measurements this project has already retained. For each, determine what machine and what conditions produced it, from whatever the record holds. Compute the spread within a single machine and the spread across machines, and compare the two.

**Why it is small.** Reading existing data, no new runs.

**What it will not cover.** If the records do not say what machine they came from, the answer is that the history is unusable — which is a real and useful finding, and would redirect this toward the isolation option rather than refining the statistics.
