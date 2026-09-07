---
type: Assumption
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion
[[Ask five operators whether they would emit firing times off-host to be told the loop stopped]]

**Risk category: viability.**

The belief, stated so it could be false: an operator who chose a product that ships `remote.enabled: false` will nonetheless turn on a channel that emits the fact and timing of every firing to a third party, in exchange for being told when firings stop.

**How it could turn out false.** The tree already carries "Connecting my systems of record could leak or corrupt them" and "Remote push optional and off by default" — a recorded preference for local-only operation that this candidate asks the operator to give up. If that preference is strong, the alerting never gets enabled, and the candidate is not a worse detector than its siblings but a dead one. The failure is quiet: the feature ships, nobody switches it on, and its detection rate looks like zero for a reason that has nothing to do with whether it works.

**Why this is the riskiest belief under this solution and not its feasibility.** Whether a ping can be sent and missed is not in doubt; that mechanism is ordinary and well understood. What is in doubt is whether anyone will accept the trade. This candidate's whole advantage over its siblings — surviving a powered-off host — is worth nothing if the switch stays off.
