---
type: Assumption
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Feasibility belief, stated so it can be false:** every bar worth tripping on can be reduced to a pattern matched against a single arriving record's text, a count of the matches, and a comparison against a fixed number — with no judgement about what the record *means*.

The bar this node was distilled from happens to have that shape exactly: match `permissions to use mcp__` in one transcript record, count, compare against 1. If most bars do, ingest can carry the check with no model in the path and no per-record cost worth measuring.

It could be false in two distinct ways, and they need separating. A bar may need **more than one record** to evaluate — "113 across 34 sessions" is a corpus statistic, not a property of any single arrival, so a per-record tripwire cannot express it at all and can at best flag a contributor to it. And a bar may need **judgement about the record's content** — "the section was present in this pass's opening context" is a fact about a prompt, not a pattern in a friction line. If the bars on this tree are mostly of those two kinds, ingest is the wrong place for this check and this whole candidate falls with the assumption.
