---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least half the sources used in the last 3 months can push on their current
  plan.
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the sources holding experiment data can push. If most are spreadsheets, free-tier survey tools, or things a person runs by hand, an endpoint has nothing to receive and the whole route serves a minority of cases.

**Risk category: feasibility.**

**Design.** List every place experiment results have actually landed over the last three months — not every place they could land. For each, check the documentation for a webhook, callback, or outbound integration on the plan the operator is actually on. Count.

**Why it is small.** An afternoon of reading documentation against a list that already exists, and it decides whether to build a listener before anything is built.

**What it will not cover.** It reads capability, not reliability. A source that can push may push unreliably, and a missed delivery is invisible in a way a failed pull is not — that is a separate question this does not touch.

## 2026-09-01 unattended sweep — examined for an instrument, and it cannot take one

Three lines, so no future pass re-derives this. This test was named in the residue of eight genuinely-unexamined tests on "The biggest queue on my report is one the surface reading it to me has no tool to clear". It has now been examined.

**Verdict: not repo-answerable.** The measurement is a person reading third-party product documentation — webhook, callback or outbound integration support — against the plans the operator is actually paying for, for every place experiment results have landed in the last three months. Nothing in this product's own vitest suite can observe another vendor's capability, and the list of sources is not on disk here. An instrument pointed at a spec file would fail today for a reason with no bearing on the threshold.

**What would make it cheap anyway.** Its own body says an afternoon of reading against a list that already exists, and that it decides whether to build a listener before anything is built. The blocker is not cost, it is that nobody has been asked; and this node carries no `lane:` field, so it sits in neither the ask queue nor any humans-required count.

_Nothing was executed, no instrument set, no lane set, no rung moved, no status changed. Read first-party from disk during the 2026-09-01 unattended sweep._
