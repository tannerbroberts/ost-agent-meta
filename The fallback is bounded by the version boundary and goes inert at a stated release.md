---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  The legacy signal is consulted only for items created before the version
  boundary and is ignored for items created after it; the fallback is inert past
  a release named in code rather than in a comment; and any item counted done by
  the legacy signal alone is reported as such rather than being
  indistinguishable from one the new ledger counts.
instrument: npx vitest run test/ost/legacy-signal-fallback-bounds.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, aimed squarely at the cost this node names against itself.**

**The assumption under test.** Not whether the union works — that is the sibling's question — but whether the *bounded* version the node proposes in one line is actually buildable as a bound rather than as a good intention. The node is unusually clear-eyed about its own failure mode: "two accounting schemes must both be understood forever, the union rule quietly becomes the real definition of done, and the next upgrade inherits three dialects instead of two. That is how compatibility layers become the thing nobody can remove." The bounded version caps that "at the price of a deadline someone has to honour", and a deadline nobody encodes is not a deadline.

**Why each clause is a clause.**

1. *Consulted only before the boundary.* An unbounded OR is the version this node argues against. If the fallback applies to items created after the new ledger shipped, it is not a compatibility layer, it is the definition of done.
2. *Inert past a release named in code.* This is the whole bounded proposal. A stated release in prose expires when someone remembers; a stated release the code reads expires whether anyone remembers or not. The difference is the difference between a bound and a hope.
3. *Legacy-counted items are distinguishable.* Without this, nothing can ever measure how much the fallback is actually carrying, so nobody can tell whether dropping it is safe — which is exactly how a temporary layer becomes permanent. It also makes the sibling's question answerable: you cannot judge whether the reopened items were genuinely finished if you cannot list which ones the union rescued.

**What is red today.** No fallback exists, so clauses 1 and 3 fail on a missing mechanism. Clause 2 is the one that would go red against the obvious implementation: an OR added to fix a live symptom has no expiry, because the expiry is not what anyone was trying to fix that day.

**What a green result does NOT settle, and it is the node's own distinguishing assumption.** Whether the union is *correct* — "if the new ledger deliberately narrowed what counts as done, then the union does not fix a bug, it reintroduces one." A perfectly bounded fallback around a wrong rule is a wrong rule with a deadline. That question is "Judge the eighteen reopened items — were they genuinely finished", which needs someone to look at eighteen items and say whether they were finished, and no exit code substitutes for that judgement.

It also does not settle the bet the node says the choice really is: how many more accounting changes are coming. One more and "Migrate the old accounting into the new ledger on first run, and record that it happened" wins; several and each is another permanent branch. That is a forecast, not a measurement.

**Lane: compute-only.** Fixture items either side of the boundary and a clock the test controls; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass from the node's own bounded variant. Nothing here was run.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/legacy-signal-fallback-bounds.test.ts` — No test files found, exiting with code 1
