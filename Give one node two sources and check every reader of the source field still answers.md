---
type: AssumptionTest
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  A fixture node carrying 2 sources is read by all 5 source-consuming surfaces —
  the rollup, ost_next_work, check, debt and status — with 0 throwing and 0
  silently reporting only the first source. The rollup's distinct-source count
  for that node's bucket must move by exactly 1 when the second source is one no
  sibling cites, and by 0 when it duplicates one.
instrument: npx vitest run test/evidence/multi-source-node.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Whether the existing readers survive a list-valued `source` is a property of committed code, settled by constructing one fixture node and calling each reader. No person is the measurement.

**What the spec must do.** Build a vault fixture with one node carrying two sources, then exercise each of the five surfaces that consume the field. Two distinct failures must both be caught: a reader that *throws* (loud, easy) and a reader that *quietly takes the first element and reports it as the whole truth* (silent, and the one that would ship). The rollup's source-count assertions exist to catch the second, because a rollup that keeps saying "1 source" for a two-source node is the exact shape of a passing test over a broken reader.

**Why this is red today.** `test/evidence/multi-source-node.test.ts` does not exist, and neither does list-valued `source` — the field is a string, so there is nothing to construct the fixture from. This is a `no-spec` red and carries that weakness: it fails identically to any other unwritten spec. The threshold above is what makes it a build permit rather than a filename, per `confirmPermit`'s handling of threshold-bound `no-spec` runs.

**What a green run would NOT settle, and this matters more here than usual.** It answers only the mechanical half of the parent assumption. It says nothing about the semantic question the assumption raises explicitly — what rung a node resting on three sources of differing standing should be capped at. Every reader could survive perfectly while the ladder quietly starts giving nodes a ceiling nobody chose. A builder reading a green here should treat the rung question as open, not answered.
