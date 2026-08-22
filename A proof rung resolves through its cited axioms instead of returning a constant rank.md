---
type: AssumptionTest
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 3 assertions pass: a conclusion citing 2 axioms at `stated` and
  `assertion` resolves to `assertion`; the same conclusion citing 2 axioms both
  at `stated` resolves to `stated`; and `believabilityRollup` over a set
  containing 1 such conclusion reports a `weakest` that reflects the resolved
  rung rather than a constant.
instrument: npx vitest run test/evidence/proof-lane-rung.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** at least 3 assertions pass — (1) a conclusion citing 2 axioms at `stated` and `assertion` resolves to `assertion`; (2) the same conclusion citing 2 axioms both at `stated` resolves to `stated`; (3) `believabilityRollup` over a set containing 1 such conclusion reports a `weakest` that reflects the resolved rung rather than a constant. Fewer than 3 refutes the assumption as stated.

**What this measures.** Whether a rung whose weight is a function of citations can live in `src/knowledge/believability.ts` alongside five rungs whose weight is an array index. Assertions (1) and (2) are the same conclusion node with different citations: if both come back with the same rung, the lane is a constant wearing a derived rung's name, and the solution's central claim — "believable exactly as far as the axioms" — is not what got built.

**Why it fails today, named from the code rather than assumed.** `rungRank` is a lookup into a `Map` built from the ladder array's indices and returns one integer per id; there is no code path by which a node's rung depends on anything the node cites. `weakestRung` implements exactly the fold this test needs and is never called across a citation edge. `classifyProvenance` floors any unrecognised prefix. All three read first-party this pass.

**Honest limit on this instrument, stated because the distinction matters here.** `test/evidence/proof-lane-rung.test.ts` does not exist, so this run files as `no-spec` — it fails for the reason any unwritten spec fails, and it does not by itself distinguish this question from another. What makes it a working build permit rather than a placeholder is the bound threshold above: `confirmPermit` keeps a permit on a `no-spec` run when `thresholdBound` holds, and the three assertions are specific enough that a builder has a definition of done without further instruction. Writing an assertion-specific red is not reachable from this surface — the instrument grammar admits one whole spec file and no `-t` filter, and no agent tool here authors a spec file.

**What a green here would NOT settle.** Feasibility only. It says nothing about whether the founder wants proof-shaped truth on the ladder at all, whether the doctrine change is one the founder will accept, or whether anyone would author axioms — those sit with the sibling assumption "An axiom's owner will stand by it when a derivation from it bites" and are a person's to answer.
