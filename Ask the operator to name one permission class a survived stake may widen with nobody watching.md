---
type: AssumptionTest
created: '2026-08-10'
evidence: assertion
lane: humans-required
threshold: >-
  The operator names at least one concrete permission class, in writing, that
  may widen automatically after a stated number of survivals; zero named classes
  fails the assumption.
---
#AssumptionTest #unvalidated #evidence/assertion

**Small, fast test of one belief.** In one short session, show the operator a mocked autonomy-ledger entry: a claim, the instrument it survived, the count of survivals. Ask one question: name a permission class this record may widen with no fresh approval at the moment of widening, and the survival count that earns it.

**Pass:** at least one concrete class named in writing (e.g. "may run read-only probes from the pre-authorized list without asking"). **Fail:** the operator wants the ledger as information but reserves every widening for manual approval — the ledger is then a log, not an autonomy mechanism, and the solution's premise falls.

**What this does not settle.** A pass is one operator's stated intent (rung: stated at best), not observed behavior over weeks away, and not feasibility of enforcing the widened grant.

A person outside the building is the measurement here: The operator is irreducibly the measurement: what they will pre-authorize while away is their decision, not derivable from code or the vault.
