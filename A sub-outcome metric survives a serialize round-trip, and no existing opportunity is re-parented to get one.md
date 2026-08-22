---
type: AssumptionTest
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 3 assertions pass: a node carrying a sub-outcome metric survives 1
  serialize→deserialize round-trip with the metric string intact; an Opportunity
  nested under another Opportunity is accepted by the write path with 0 changes
  to the hierarchy rules; and 0 of the vault's existing opportunities require
  re-parenting for the layer to exist.
instrument: npx vitest run test/ost/sub-outcome-layer.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** at least 3 assertions pass — (1) a node carrying a sub-outcome metric survives 1 `serialize`→`deserialize` round-trip with the metric string intact; (2) an Opportunity nested under another Opportunity is accepted by the write path with 0 changes to the hierarchy rules; (3) 0 of the vault's existing opportunities require re-parenting for the layer to exist. Fewer than 3 refutes the assumption, and which one fails says which half of this node's parent solution was right.

**What each assertion is for.** (1) is the only one expected to be hard: `serialize` writes only its enumerated keys and `deserialize` lifts only its enumerated keys, so an unenumerated `metric:` is dropped silently on the next tool write — no error, no warning, the field simply is not there afterwards. (2) and (3) are written to **fail loudly if the parent assumption is wrong**: if the layer genuinely needs its own `Layer` member, then nesting is not free, the hierarchy rules do change, and these two stop being the formalities this node claims they are. They are the falsifiers, not the padding.

**Why it fails today, named from the code.** `OstNode` has no metric or target field; the nearest is `threshold`, documented as an AssumptionTest field read by `askedOf`. `serialize` builds `data` from a fixed key list; `deserialize` reads a fixed key list back. Both read first-party this pass.

**Honest limit on this instrument.** `test/ost/sub-outcome-layer.test.ts` does not exist, so this run files as `no-spec` — it fails for the reason any unwritten spec fails, and does not on its own distinguish this question from another. The bound threshold above is what makes it a working build permit rather than a placeholder. An assertion-specific red is not reachable from this surface: the instrument grammar takes one whole spec file with no `-t` filter, and no tool here authors a spec.

**What a green here would NOT settle.** Feasibility and cost only. It says nothing about whether a sub-outcome layer is legible to a reader, whether two practitioners would place the same opportunity under the same one, or whether the founder wants the layer at all — those sit with the sibling assumption "Two practitioners place the same opportunity under the same sub-outcome" and are a person's to answer. It also does not settle the sub-outcome-versus-milestone naming question this solution's Issues section holds open for a human; it only removes recursion from the list of things that distinguish them.
