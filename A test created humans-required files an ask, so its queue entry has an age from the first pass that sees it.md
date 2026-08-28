---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-28'
evidence: assertion
threshold: zero queue entries with a humans-required lane and a null askedAt
instrument: npx vitest run test/ost/ask-filed-at-creation.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** This asks what the code does, not what a person would do.

**What the spec must assert.** Over a fresh fixture vault, create an AssumptionTest with `humansRequired` supplied at creation time — the `ost_create_node` path, not `flagHumansRequired` — with an injected clock at a fixed T0. Then, with the clock advanced eleven days, read the queue via `readPendingAskQueue` and via `computeNextWork(...).outstandingAsks`, and assert on that entry:

- `askedAt` equals `T0.toISOString()` — not `null`;
- `ageDays` equals `11` — not `null`;
- `command` contains `ost-agent result "<the test's title>"`.

Add the non-vacuity control the sibling spec already uses: a test created with no lane at all must stay off `outstandingAsks` entirely, so the assertion cannot pass by the queue simply admitting everything.

**Why it fails today.** `src/ost/pending-asks.ts` sources `askedAt`/`ageDays` from the ask ledger alone, while queue membership also comes from the lane. `src/ost/lanes.ts` files an ask from the lane-setting path; nothing files one when the lane arrives with the node at creation. So the entry exists and its age is `null`, and the first two assertions above go red on today's behaviour rather than on an absent feature.

**Honest limit on the red, stated because it changes what a builder should conclude.** The spec file named above does not exist yet, so today this command fails as `no-spec` — the same way it would fail for any question anyone wrote on that path. It mints no build permit, and it is not finished work: what makes it finishable is that the assertions are fully specified above and are predicted to fail against `src/ost/pending-asks.ts` as it stands. The pass that wrote this could read the repository but could not write to it. Whoever picks this up should write the spec, watch it go red for the reason stated, and only then treat it as a definition of done.

**What a green here would not settle.** Only that entries are dated. Whether a dated queue is one the operator ever empties is the sibling belief "An operator will actually visit a queue that never chases them", and no exit code reaches it. Feasibility answered mechanically leaves desirability, viability and usability exactly where they were.

**If it comes back green on first run,** the reading beneath this node is wrong — creation does file an ask somewhere unread — and the real explanation for 52 of 52 null ages is elsewhere. That is a useful outcome and should be recorded as a refutation, not discarded.
