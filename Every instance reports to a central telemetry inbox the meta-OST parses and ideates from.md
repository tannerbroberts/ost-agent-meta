---
type: Solution
status: unvalidated
source: 'human:conversation:2026-07-26'
created: '2026-07-26'
evidence: assertion
---
#Solution #unvalidated #founder-provided #evidence/assertion
[[Operators will let their vault report outward at all]]
[[An instance can deliver to the central inbox on what it already holds, with its provenance intact]]

**Mechanism (founder-provided, 2026-07-26):** All instances of the OST-Agent report to a central telemetry inbox belonging to the OST-Agent that runs the OST *for* the OST-Agent (this vault). The meta-OST parses that inbox, ideates on what arrives, and generates yet more solutions — fleet experience becomes discovery input automatically, with no human carrying it.

**Contrast with existing neighbors:** "Raw-first telemetry store with summaries as derived views" is about retention fidelity in one store; this is about *routing* — every instance's stream converging on the meta-OST's inbox as a consumer. "Operator-owned local event log with consented raw export" frames consent for *other people's* instances; founder-run fleet instances need no consent negotiation, which removes that solution's main constraint. "Backpressure-tolerant ingest channel that preserves provenance under load" is the load-survival layer a fleet inbox would sit on. "Autonomous web-research loop that files findings into the inbox" already establishes the inbox-as-ingest pattern this generalizes to instances.

**Key assumptions (explicit, untested):** (feasibility) instances can identify and reach a central inbox without new credentials or infrastructure beyond the compute already in hand; (feasibility) the meta-OST's existing map/ideate passes can keep up with N instances' output without drowning the 19-item inbox backlog dynamic in noise; (viability) fleet telemetry converging on one vault preserves per-instance provenance well enough to remain believable evidence; (desirability) founder-run instance streams — self-generated, assertion-heavy — actually raise the tree's evidence quality rather than deepening the echo chamber the usage-feed opportunity explicitly warns against.

**Rung honesty:** founder-provided solution, entered unvalidated — its provenance implies no promotion.

## Definition of done

"A fleet instance reaches the inbox with no new credential, and its provenance survives the trip"

```
npx vitest run test/adapters/fleet-inbox-provenance.test.ts
```

Green means the first two of the four assumptions listed above are settled: two instances deliver to one inbox on the compute and credentials they already hold, and every delivered item stays attributable to the instance that produced it, with an item that loses its attribution refused rather than ingested anonymously. That last clause is the load-bearing one — ten instances agreeing and one instance repeated ten times are the same stream once attribution is flattened, and every rung computed over it would be wrong in the flattering direction.

It settles neither of the other two. Whether the meta-OST's passes keep up with N instances is a load question owned by "Backpressure-tolerant ingest channel that preserves provenance under load". And whether founder-run, self-generated, assertion-heavy streams raise the tree's evidence quality or deepen the echo chamber is untouched by any exit code: green here is fully compatible with the resulting evidence being worthless, and only outside operators distinguish the two.

## History
- 2026-08-05 unlinked "Ask five prospective operators whether they would let their vault report outward" — moved under "Operators will let their vault report outward at all" — the belief this test measures now has a node of its own
- 2026-08-05 unlinked "A fleet instance reaches the inbox with no new credential, and its provenance survives the trip" — moved under "An instance can deliver to the central inbox on what it already holds, with its provenance intact" — the belief this test measures now has a node of its own
