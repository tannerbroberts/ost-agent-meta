---
type: Solution
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Candidate solution (unvalidated).** The run records a cheap fingerprint of the ground it is standing on — `HEAD`, and the mtime/size of every file it has read this pass — and re-samples it between steps. When the fingerprint moves, the run is interrupted with what moved, at the moment it moved, rather than discovering it several steps later through an unrelated failure.

**Approach:** *notice the movement itself*, which is what this opportunity's own framing asks for: "learn that the ground moved at the moment it moves, from something that watches for it".

**Contrast with siblings.** This one watches and reports; "Classify the failed match by comparing the file against the run journal's recorded read" does nothing until a write has already failed and then explains it; "Declare the files a run intends to touch, and refuse to start when another writer already holds them" tries to stop the collision happening at all. The sentinel is the only one of the three that can catch movement in a file the run has read but not yet written — which is the case in the observed session, where HEAD had moved to a merge and roughly fourteen files carried seconds-old changes before any edit was attempted.

**Where it is weakest, stated so it can be judged.** Sampling has a window: movement between the last sample and the next write is still invisible, so this narrows the gap rather than closing it. It also cannot distinguish a merge landing from the operator saving a file in an editor, and an unattended run interrupted by the latter is a false stop. Both are reasons the threshold beneath it is about how often sampling would actually have fired before the damage, not about whether sampling is possible.

⚠️ Unvalidated, and ideated by an agent from its own session record. This grounds usability, not that anyone outside wants it.
