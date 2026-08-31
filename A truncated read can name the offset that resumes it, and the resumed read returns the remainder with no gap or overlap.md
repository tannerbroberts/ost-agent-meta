---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

The candidate assumes a capped read can hand back a resumption point that actually works — that the head plus the slice starting at the named offset reconstitute the artifact exactly, with nothing dropped between them and nothing served twice.

Stated so it could be false: it is false if the transformations a read applies before capping make the offset meaningless. `src/product/repo.ts` runs `redactSecrets` over the whole file and then slices the redacted text, so an offset is an index into redacted content whose length is not the file's length. A resumption offset computed against the wrong string silently skips or repeats a region, and the reader has no way to notice — which is the same silent-failure direction the candidate already names as its main cost, arriving through a different door.

This is the half a spec can reach. It is not the belief that decides the candidate — that one is whether readers actually check the truncation flag rather than treating a partial body as whole, which needs a corpus of real sessions and a person's reading of them.
