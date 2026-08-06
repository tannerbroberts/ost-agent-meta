---
type: Opportunity
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[A drift sentinel that samples HEAD and file mtimes between steps and interrupts on movement]]
[[Classify the failed match by comparing the file against the run journal's recorded read]]
[[Declare the files a run intends to touch, and refuse to start when another writer already holds them]]

Observed in one session with the collision still in progress: two `Edit` calls returned "String to replace not found in file" — one naming `src/knowledge/web-trust.ts:62` — and the agent then had to stop and ask, having worked out for itself that "another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago)". The same failed-match error recurs in other sessions with no such diagnosis attached.

The tell is that the diagnosis was reconstructed by hand from HEAD and file mtimes, after the fact. The need is to learn that the ground moved at the moment it moves, from something that watches for it — not from a string comparison failing for a reason that is indistinguishable from the agent having quoted the file wrong.
