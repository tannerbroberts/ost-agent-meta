---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At most 6 forms, with fewer than 4 breaking changes across all of them in the
  last year.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the set of credential forms is small and stable enough to maintain. Every accepted form is an integration, and each one changes on someone else's schedule — so the ongoing cost is the question, not the initial build.

**Risk category: feasibility.**

**Design.** Enumerate the credential forms this tool would need to accept for the services it actually touches. For each, look back a year through changelogs and deprecation notices and count breaking changes. Total the annual maintenance events.

**Why it is small.** Reading public changelogs for a handful of services, an afternoon.

**What it will not cover.** Past change rate predicts future change rate poorly for services that are themselves young. It also says nothing about the security exposure of handling many forms, which is the other half of the objection and needs a different test.
