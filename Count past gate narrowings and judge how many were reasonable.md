---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Fewer than 2 narrowings per month on average.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that narrowings are rare enough to route through a person. If they are frequent and mostly reasonable, a human bottleneck creates pressure to set gates loosely from the start so they never need narrowing — a worse outcome reached by a respectable route.

**Risk category: viability.**

**Design.** Search the commit history for every change that reduced what a gate covered — an added exclusion, a skipped case, a relaxed threshold. Count them and date them. For each, a person judges whether it was reasonable. Compute the rate per month and the share judged reasonable.

**Why it is small.** The history exists; this is reading and judging it.

**What it will not cover.** The judge is the person who made most of these changes, which biases toward reasonable. The rate is the more reliable half of the finding.

A human runs this and records the result.
