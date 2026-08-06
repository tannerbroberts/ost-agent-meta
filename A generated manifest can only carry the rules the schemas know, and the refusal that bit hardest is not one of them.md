---
type: Assumption
source: 'TRANSCRIPT:1744f10a-e7ce-4e46-a573-a1d99c44960c'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Measure what fraction of recorded refusals a schema-derived manifest could have named]]

**The belief, stated so it could be false.** Every precondition that actually costs a pass a turn is derivable from the tool surface's own schemas, so a manifest generated from those schemas would have named the rules that sessions actually collided with.

**Why it is the riskiest one.** The solution's whole cost argument rests on generation-from-schema — its own body says a hand-written manifest "becomes a second statement of the rules that drifts from the first". But the single most frequent refusal in this vault's corpus, "File has not been read yet", is a *harness* rule about Edit and Write. It is not expressed in any MCP tool schema, and it may not be expressed in the harness's tool schemas either. If the rules that bite live outside the schemas, a generated manifest is complete with respect to the wrong set and the solution addresses roughly none of the observed friction while looking like it addresses all of it.

**What class this is.** Feasibility. It is answerable from the repository — enumerate the distinct refusal strings the transcript corpus recorded, and ask of each whether a generator with only the schemas in hand could have emitted a rule covering it. No customer is involved and none should be asked.

**How it could come out false.** Plausibly: the read-before-write handshake, the response-size cap, and the "no such tool available" denials are all enforced by the runtime rather than declared by a schema. That is three of the corpus's top four classes. A coverage number well under half would not refine this solution, it would refute its cost claim.
