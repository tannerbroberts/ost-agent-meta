---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Resetting the shared checkout to main before every firing doesn't clobber a still-running firing's in-flight work]]
[[Resetting the shared checkout to main before every firing never discards in-flight work a concurrent firing depends on]]

Before any firing (build or discovery loop) reads which automation script to run, force the shared working directory back to `main` — `git checkout main && git reset --hard origin/main` (or equivalent) — so a prior firing's transient branch, and any edit it made to `examples/automation/*.sh` on that branch, can never carry forward as the next firing's executable policy. Cheapest mechanism: a few lines at the top of the loop's entry point, no new infrastructure, no change to the single-checkout model. Does not stop a build session from editing a script mid-session and running the edited version within its own firing — it only stops that edit from persisting into the *next* firing.

## Issues
- 2026-08-17 Assumption surfaced ("Resetting the shared checkout to main before every firing doesn't clobber a still-running firing's in-flight work") but its test is not created: it's a feasibility/safety question the repository can answer, and naming `humansRequired` just to satisfy the tool would misstate that. This unattended sweep holds no `ost_read_repo` grant, so it cannot ground a real instrument. Needs an attended pass (or a human) with repo sight to write the spec-file instrument.
