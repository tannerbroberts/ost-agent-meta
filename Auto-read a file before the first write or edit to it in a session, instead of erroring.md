---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Auto-reading a file before write doesn't mask the exact race condition the guard exists to catch]]
[[Editor tooling can auto-read a file transparently before a first Write Edit without weakening the guard's protection against blind overwrites]]

When Write or Edit targets a file the session has not read yet this run, have the harness perform the read itself first (transparently, no extra turn) rather than refusing with a tool_error. The guard's purpose — never clobber content the session hasn't seen — is preserved; only the burned turn and retry disappear.

**Compared to the alternatives.** This is the only candidate that removes the friction event entirely rather than helping the session recover from it faster. Its risk is the guard's whole point: if the auto-read happens invisibly, a session may still act on stale assumptions formed before that read (e.g. a plan made from a stale summary), so the fix has to genuinely feed the fresh content into the session's context, not just satisfy the guard mechanically.

## Issues
- 2026-08-17 Assumption surfaced ("Auto-reading a file before write doesn't mask the exact race condition the guard exists to catch") but its test is not created: this is a feasibility question the repository can answer (how the current guard is implemented and where the race window actually is), and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.
