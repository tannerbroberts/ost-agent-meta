---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Every invocation of the committed bundle is preceded by a build step, and a new consumer without one fails the census]]

Feasibility belief: whatever today reads dist/ost-agent.mjs straight out of a checkout (a publish step, a deploy script, another firing) can be changed to run the build first, without breaking a path this pass doesn't have visibility into.
