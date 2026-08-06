---
type: Opportunity
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

Machine-recorded: in 583 tool invocations on 2026-08-05, exactly one call failed, and it was `ost_read_repo` — "no product repos configured — add local repo paths under `product.repos` in ost.config.yaml". The operator does not discover the gap at setup, when it is cheap to fix; they discover it in the middle of a pass, at the moment the agent reached for the product and found nothing there. Everything downstream of that reach — instruments grounded in real modules rather than invented paths — is silently degraded rather than blocked, so the pass reports success while working blind.

The need is to know that a configured sense is actually wired before a pass depends on it, rather than after.
