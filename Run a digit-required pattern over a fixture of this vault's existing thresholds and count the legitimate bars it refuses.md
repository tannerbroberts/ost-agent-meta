---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  0 of the fixture's fixed-bar thresholds are refused by the pattern, and 1 of 1
  digit-less thresholds is refused by validateToolInput with a problem naming
  threshold
instrument: npx vitest run test/security/threshold-schema-pattern.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Feasibility test of one belief: that the numeric-bar rule can live on the `threshold` property of `ost_create_node`'s input schema as an unconditional pattern, reported per field by `validateToolInput`, without refusing thresholds a human reads as a fixed bar.

**What the spec does.** Holds a fixture of threshold strings copied from this vault's AssumptionTests — digit-bearing bars ("at least 5 of 20 book a kickoff"), spelled-out bars ("at least five of twenty"), and non-numeric bars ("the guard refuses the write"). Reads the `ost_create_node` schema from `buildOstTools`, asserts the `threshold` property carries a pattern, runs each fixture string through `validateToolInput` (the server's existing per-field path, read this pass in `src/mcp/server.ts`), and asserts: every fixed-bar string passes, and a digit-less one fails with a problem whose text names `threshold`.

**Why it is red today, and which kind of red.** The spec file does not exist — a **no-spec red**, declared as such: vacuous until written, no permit. Once written, it is red on a specific assertion: the current schema carries no pattern on `threshold`, so `validateToolInput` reports nothing and the check happens later, by hand, in the tool body. The fixture's non-numeric bars are the part most likely to keep it red after a naive build, which is the point: a pattern that refuses "the guard refuses the write" has traded one wrong refusal for another.

**What it does not settle.** Whether an unconditional rule is the right rule — that is a judgement about what a threshold is for — and nothing about how the message reads to a session, which the reworded-refusal sibling tests.
