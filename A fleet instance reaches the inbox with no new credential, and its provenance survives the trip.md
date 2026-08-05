---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  Two fixture instances deliver to one inbox using only the compute and
  credentials each already holds; every delivered item is attributable to the
  instance that produced it after the merge, with no two instances' items
  collapsing into one indistinguishable stream; and an item that loses its
  instance attribution in transit is refused rather than ingested anonymously.
instrument: npx vitest run test/adapters/fleet-inbox-provenance.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, and it is the first two of the four assumptions the node lists explicitly.**

**The assumption under test.** The node names four key assumptions and marks all of them untested. Two are mechanical and are what this settles: that *instances can identify and reach a central inbox without new credentials or infrastructure beyond the compute already in hand*, and that *fleet telemetry converging on one vault preserves per-instance provenance well enough to remain believable evidence*. The other two are not, and are dealt with below.

**Why provenance is the clause that carries the weight.** This tree's whole believability apparatus is a function of what a node's source has earned as an actor. A fleet stream that arrives with its per-instance attribution flattened does not merely lose a label — it makes every rung computed over it wrong, because ten instances agreeing looks like corroboration and one instance repeated ten times looks the same. The refusal clause is there for the same reason the vault refuses a result with no name on it: an item that cannot say which instance produced it is indistinguishable from an item nobody produced, and ingesting it anonymously is the failure that cannot be detected downstream.

**Why "no new credential" is testable and not just a hope.** The node's contrast with [[Operator-owned local event log with consented raw export]] rests on founder-run fleet instances needing no consent negotiation, which removes that solution's main constraint — but removing the *consent* constraint does not remove the *reachability* one, and the node asserts reachability without evidence. A fixture with two instances and no shared secret either delivers or it does not.

**What is red today.** There is no fleet inbox and no routing, so the delivery clauses fail on a missing mechanism. The refusal clause is the one that would go red against a working first implementation: appending arriving items to a shared inbox is the obvious build, and the obvious build has no reason to refuse an item whose attribution went missing.

**What a green result does NOT settle — and here the node's own fourth assumption is the serious one.** Whether founder-run instance streams *raise* the tree's evidence quality or deepen an echo chamber. Every item in such a stream is self-generated and assertion-heavy by construction, which is precisely what the usage-feed opportunity warns against, and no exit code distinguishes a fleet that is learning from a fleet that is agreeing with itself in ten voices. Green here means the plumbing is sound and provenance is intact; it is entirely compatible with the resulting evidence being worthless. That question needs outside operators, which is [[Ask five prospective operators whether they would let their vault report outward]] and, more to the point, the outcome's own external-returning-operators instrument.

Nor does it settle the third assumption — that the meta-OST's map and ideate passes can keep up with N instances without drowning. That is a load question, and [[Backpressure-tolerant ingest channel that preserves provenance under load]] is the node that owns it.

**Lane: compute-only.** Two fixture instances and one inbox; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass from the node's own list of untested assumptions. Nothing here was run.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/adapters/fleet-inbox-provenance.test.ts` — No test files found, exiting with code 1
