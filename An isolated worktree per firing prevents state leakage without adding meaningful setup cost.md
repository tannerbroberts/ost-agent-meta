---
type: Assumption
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility/cost assumption: creating a fresh worktree per firing actually stops one firing's edits (including an edit to the automation scripts) from being inherited by the next firing's checkout, and the setup/teardown cost of doing this every firing is small enough not to matter against how often firings run.

This is answerable from the repository — time how long a worktree create/remove cycle takes against the shared-checkout pattern it replaces, and confirm a worktree genuinely isolates an in-progress edit. No customer interview is needed; a human or an attended pass with repo sight should confirm before treating this as tested.
