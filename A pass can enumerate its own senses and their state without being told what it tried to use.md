---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility. The census is only cheap if it is derivable — read the config, read the tool grant, and state each sense as configured/wired/granted without the pass having to instrument every call site.

The precedent says it is derivable for one half: `ost_ingest_inbox` already reports six channels including the two that are off, and it does that from config alone, without any channel having been tried.

Stated so it can be false: the read-senses are not symmetric with the write-channels. Whether `ost_read_repo` is usable depends on config; whether `Glob` on the product directory is usable depends on a harness grant the server may not be able to see. If a pass cannot enumerate its own tool grant from inside itself, half the census has to be built from observed denials — which means it can only report senses something already reached for, and a sense nothing tried is indistinguishable from one that worked.

That failure mode is precisely the one this pass exhibited: `ost_check` was never called, so nothing knows whether it would have been refused.
