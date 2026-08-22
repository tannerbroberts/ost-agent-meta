---
type: Assumption
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility belief, and it is the mechanical form of the failure mode this node already names at birth.

The node says the ledger must judge widening "against claim difficulty or claim usefulness, not claim count — otherwise this is the 'agent narrows its own capability to get past a gate I set' pain, inverted." That risk is stated as a design caution. On this product it is sharper than a caution, because the cheapest possible claim is not merely available — it is the only kind an agent surface can author.

The chain, from committed code read this pass:

- The instrument grammar admits exactly one form, `npx vitest run <path>.test.ts`, and refuses shell punctuation — so no agent can point at an assertion inside an existing file.
- No agent surface has a tool that writes a spec file.
- Therefore an agent's instruments name paths nobody has written, and `runInstrument` files those as `no-spec`.
- A `no-spec` run measures nothing. `observedRed` does not match it, by design.

So an agent that could widen its own permission by accumulating survived claims would be accumulating them out of the one artefact it can mint at will and that nothing can refute. Claim count is not merely a weak proxy here; it is a proxy the claimant controls end to end.

Stated so it could be false: the record distinguishes a claim that was staked and survived a real measurement from one whose spec was never written, and the ledger can be built to count only the former.

What makes it plausible: the distinction already exists in the log — `**red**`, `**green**` and `**no-spec**` are separate markers, and `currentObservations` filters on the exact command so an instrument swap cannot inherit another command's history. What makes it doubtful: reds recorded before the `no-spec` marker existed still read `**red**` and are indistinguishable in the log from genuine ones; `confirmPermit` handles that by re-running the command, which a ledger reading history alone would not do.
