---
type: Solution
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

When Write or Edit targets a file the session has not read yet this run, have the harness perform the read itself first (transparently, no extra turn) rather than refusing with a tool_error. The guard's purpose — never clobber content the session hasn't seen — is preserved; only the burned turn and retry disappear.

**Compared to the alternatives.** This is the only candidate that removes the friction event entirely rather than helping the session recover from it faster. Its risk is the guard's whole point: if the auto-read happens invisibly, a session may still act on stale assumptions formed before that read (e.g. a plan made from a stale summary), so the fix has to genuinely feed the fresh content into the session's context, not just satisfy the guard mechanically.
