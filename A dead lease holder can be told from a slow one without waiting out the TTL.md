---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility, and it is what separates leasing from a timeout with better manners.

**Stated so it can be false.** If the only way to know a lease holder is gone is that its TTL expired, then leasing does not remove the failure this opportunity is about — it bounds it. A run that dies at minute one still blocks the workspace until the TTL elapses, and the loop still burns firings on a workspace it cannot have. Under that reading, leasing buys nothing over reconciliation except a longer outage, and costs considerably more to build.

For it to be true, liveness has to be observable directly: the holder's process still existing, a heartbeat written recently enough to be unambiguous, or the run's own journal still being appended to. Any of those turns "assume dead after 60 minutes" into "know dead in seconds", which is the difference between this candidate working and this candidate being ceremony.

**The precedent cuts both ways and should be read carefully.** This vault's config already runs a TTL lease for the firing loop — `lockTtlMinutes: 60`, commented "a firing still holding the lock after this is assumed dead". The word *assumed* is the admission: the existing mechanism does not detect death, it waits. So the product has precedent for the shape and no precedent at all for the belief stated here.

**The symmetric risk.** A liveness check that is too eager reclaims a workspace from a run that was merely slow, mid-build, and healthy — reintroducing the destructive failure that reconciliation was rejected for. This belief is therefore not "we can detect death" but the sharper "we can detect death without ever mistaking slowness for it", and only the second one makes the candidate safe.
