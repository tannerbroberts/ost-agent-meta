---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Before any firing (build or discovery loop) reads which automation script to run, force the shared working directory back to `main` — `git checkout main && git reset --hard origin/main` (or equivalent) — so a prior firing's transient branch, and any edit it made to `examples/automation/*.sh` on that branch, can never carry forward as the next firing's executable policy. Cheapest mechanism: a few lines at the top of the loop's entry point, no new infrastructure, no change to the single-checkout model. Does not stop a build session from editing a script mid-session and running the edited version within its own firing — it only stops that edit from persisting into the *next* firing.
