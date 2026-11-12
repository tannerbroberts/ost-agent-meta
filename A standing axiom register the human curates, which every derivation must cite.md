---
type: Solution
source: 'INBOX:2026-08-10-founder-theory-axioms-and-theory-space-proof.md'
created: '2026-08-10'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[An up-front authoring session produces axioms the founder still endorses when they matter]]
[[The citation index revocation needs already exists in evidenceExtents, and only its keying and its source filter stand in the way]]

Axioms are elicited up front and kept as a curated register in the vault: each entry states the axiom, who accepted it, when, and what accepting it commits the tree to. A derivation may only enter the proof lane by citing register entries; revising or revoking an axiom is a recorded act that re-opens every derivation citing it.

**Contrast with siblings.** Against "Axioms elicited at the moment a derivation needs them, one accept-or-reject ask at a time": the register pays elicitation cost before any derivation exists, buying derivations that never wait on a human, at the risk that the up-front session produces shelf axioms nobody meant deeply. Against "Borrow the axiom set from a named body of practice and let the human only veto": authorship here is fully the human's, honoring the founder's "felt-out distinction" at maximum cost in their time.

**Sharpest risk:** desirability — whether the up-front authoring session ever happens and produces axioms the founder still endorses later.

## Definition of done

"Querying the citers of one revoked axiom returns the direct citers at any layer, and not their ancestors"

`npx vitest run test/evidence/axiom-citation-index.test.ts`

Added 2026-11-12 by an unattended sweep. The test sits two nodes below this one (under the assumption "The citation index revocation needs already exists in evidenceExtents, and only its keying and its source filter stand in the way") and already carried this command; it was only missing here, where a builder reads. The test's own prose says the spec file does not exist, so the command is `no-spec` today, not an assertion-specific red — not re-probed this firing. Its four pre-committed assertions are on the test node. A green covers the revocation index only. Whether the up-front authoring session happens and yields axioms the founder still endorses is the sibling assumption's, and a person's.
