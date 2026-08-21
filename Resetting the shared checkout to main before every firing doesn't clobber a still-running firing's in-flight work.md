---
type: Assumption
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A pre-firing reset is refused while either loop's lock is live, and runs only when neither is]]

Feasibility/safety assumption: resetting the shared checkout to main before reading which automation script to run is safe only if firings never overlap — if two firings can be in flight at once, resetting the checkout out from under a still-running one destroys its uncommitted work, which is a worse failure than the unreviewed-policy problem this solution is meant to fix.

This is answerable from the repository — check whether the scheduler can ever start a firing while a prior one is still running, and if so, whether reset is scoped in a way that can't touch it. No customer interview is needed; a human or an attended pass with repo sight should confirm before treating this as tested.
