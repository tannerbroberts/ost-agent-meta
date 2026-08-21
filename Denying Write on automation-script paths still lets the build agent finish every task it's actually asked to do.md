---
type: Assumption
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[The build-pass invocation denies Write on its own automation-script paths while still granting Write elsewhere]]

Feasibility assumption: revoking Write on the automation-script paths closes the hole (a build session editing the scripts that govern every future firing) without also blocking legitimate build work that never needs to touch those paths. If normal build tasks occasionally DO need to edit automation scripts (e.g. shipping a fix to the loop itself), a blanket deny either breaks that class of work or has to be special-cased, which reopens the same hole through the exception.

This is answerable from the repository: which build tasks, if any, have historically needed to write to the automation-script paths, and whether the permission boundary can be drawn to exclude only those. No customer interview is needed — a human or an attended pass with repo sight should confirm before treating this as tested.
