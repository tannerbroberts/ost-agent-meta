---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  A fixture opportunity with exactly one sub-opportunity and zero solutions
  anywhere in its subtree is still reported as under-served; a fixture category
  with one sub-opportunity carrying three solutions is not.
instrument: npx vitest run test/ost/next-work-category-exemption.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** The false-negative rate of the cheapest rule in this branch, on the one shape that decides whether it is safe. Having a child is the exemption's entire evidence; the test asks whether that evidence survives the case where the child is empty too.

**Why it is red today.** No exemption exists — the current check reports both fixtures — so the second assertion fails immediately, and the first passes for the wrong reason. The file must assert both so the difference is visible.

**Honest limit on the instrument.** Written without repo sight; the path does not exist, so the first failure is a missing file rather than a failing assertion. See "My instruments are red because a file is absent, not because the behaviour is".

**What a green here does not settle.** Whether the exemption is preferable to rollup or to leaf redirection — that is a comparison across three candidates and this file only examines one. It also says nothing about how many real nodes in the live tree have the dangerous shape, which is a census, not a spec.
