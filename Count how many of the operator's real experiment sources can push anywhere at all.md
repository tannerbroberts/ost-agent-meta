---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least half the sources used in the last 3 months can push on their current
  plan.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the sources holding experiment data can push. If most are spreadsheets, free-tier survey tools, or things a person runs by hand, an endpoint has nothing to receive and the whole route serves a minority of cases.

**Risk category: feasibility.**

**Design.** List every place experiment results have actually landed over the last three months — not every place they could land. For each, check the documentation for a webhook, callback, or outbound integration on the plan the operator is actually on. Count.

**Why it is small.** An afternoon of reading documentation against a list that already exists, and it decides whether to build a listener before anything is built.

**What it will not cover.** It reads capability, not reliability. A source that can push may push unreliably, and a missed delivery is invisible in a way a failed pull is not — that is a separate question this does not touch.
