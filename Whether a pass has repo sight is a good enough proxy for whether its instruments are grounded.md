---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

This is the assumption that decides whether gating on repo sight is the right gate, and it is the weakest link in the candidate above it.

The belief: a pass with repo sight writes instruments grounded in real mechanisms, and a pass without it writes commands whose only red is a missing file. Gate on the former and you prevent the latter.

Stated so it can be false, and there is already counter-evidence from the pass that proposed it. On 2026-08-06 a sweep with no repo sight wrote three instruments. Two of them — for `test/ost/next-work-status-filter.test.ts` and `test/ost/underserved-subtree-count.test.ts` — assert behaviour that pass had directly observed to be absent by running `ost_next_work` and reading the nodes it returned, so they fail today on the mechanism. One, for `test/ost/disposition-ledger-shape.test.ts`, describes a wholly absent mechanism and fails on the import. Two out of three were grounded *without* the sense this gate would require, because the tree itself carried enough mechanism to predict against.

So the proxy over-blocks, demonstrably. Whether it also under-blocks — whether a pass *with* repo sight writes ungrounded instruments anyway — is unmeasured, and a gate that is wrong in both directions is not a gate, it is a tax.

What would rescue the candidate is a different gate on the same idea: require the instrument's author to state which kind of red it is, and check that the claim is present rather than checking a proxy for it. That is a strictly better design and it belongs to whoever picks this up.
