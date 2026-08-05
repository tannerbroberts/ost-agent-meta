---
type: Solution
source: 'TRANSCRIPT:ac007b7b-ac18-4a19-94f1-cb5f3c93ca42'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

One call, made before the run commits to a plan, that returns the **state** facts a plan depends on rather than the path facts a directory listing already gives: is this a git repository, does it have a remote, which of the binaries this plan will invoke are actually on PATH, is there a lockfile, has a build ever run here.

The reader pays. That is this candidate's defining property and the axis it should be compared on against its siblings — [[The scaffolder writes a manifest of what it did and did not initialise]] moves the cost to whoever created the workspace, and [[Scaffolding initialises unconditionally, so the state is never in question]] removes the variance instead of reporting it.

**Why a probe and not better error handling.** In all four captured sessions the failure was recoverable in one command; the expense was that it arrived *after* the run had already reasoned about a workspace it believed was a repository. Handling the error better still pays the planning cost. Asking first does not.

**The obvious objection, stated plainly.** A probe is a guess about which facts will matter, and a plan can depend on a fact the probe did not think to return — at which point the run is back to learning from a failure, having also paid for the probe. That is the risk worth testing before building: whether a small fixed set of state questions actually covers the failures that have happened. If it takes twenty questions to cover them, this is the wrong shape and the capability-declaration sibling is better, because there the *plan* names what it needs rather than the probe guessing.

**Relationship to existing work.** This is the state-shaped cousin of the workspace-map candidates under [[I probe for files that were never there, because nothing hands me the layout of the workspace I am in]]. Those answer "what is here"; this answers "what is true of it". Worth checking with a human whether they should be one mechanism — the 2026-08-05 pass judged them distinct enough to sit apart, since a map that listed every file in the captured sessions would still not have said the folder was not a repository.

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._
