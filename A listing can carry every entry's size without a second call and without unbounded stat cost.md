---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

The candidate above assumes a listing can hand back a size per entry as part of the call the reader was already making, and that the extra filesystem work this costs stays bounded by the entry cap that already exists rather than growing with the directory.

Stated so it could be false: it is false if sizing every entry requires work outside the listing's existing budget — a stat per entry on a directory of arbitrary size, or a read rather than a stat — in which case the listing stops being cheap and the candidate has moved the cost rather than removed it.

Grounded in what is there: `src/product/repo.ts` already slices its listing to `MAX_LIST_ENTRIES` (500) and already takes one `statSync` on the target path before deciding file-versus-directory, so the mechanism and the ceiling both exist. What does not exist is a per-entry size, and what is untested is whether the ceiling holds once one is added.

This is the half a spec can reach. It is not the belief that decides the candidate — that one is whether a reader shown a size behaves differently, which is usability and needs people.
