---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault
[[Can't tell if the generated tree is actually any good]]
[[Connecting my systems of record could leak or corrupt them]]
[[Fear the agent could take a destructive, irreversible action]]
[[Want proof no hijackable capability even exists]]
[[Worry the agent is grading its own homework]]
[[Append-only audit trail the operator can replay]]
[[Guided dry-run mode before unattended operation]]
[[Weekly what-changed-and-why digest]]

**Customer need (operator's perspective):** "I want to download the tool, run one command, then walk away and trust it to run completely unmonitored — and come back to a tree that faithfully reflects what my business is learning, with fresh candidate solutions and assumptions, and nothing unproven dressed up as proven."

The core pain is the leap of faith required to leave an autonomous agent running against real business knowledge with no one watching. Operators will only walk away if they trust both that nothing bad can happen *and* that what they come back to is honest and useful.

**Litmus (more than one way to address?):** Yes — trust can be earned through safety guarantees, faithful-representation guarantees, honesty about validation state, unattended reliability, transparency/audit trails, etc. This is a genuine need, not a solution.

This is an umbrella trust opportunity. Its more specific facets are nested beneath it as child opportunities.

_Provenance: INBOX:2026-07-22-design-goals.md (README + design spec, 2026-07-22). Distilled by autonomous OST pass; unvalidated — for human review._

_Ported from the ost-agent-vault tree (2026-07-24 consolidation). In that vault this node carried the human-authored title "Any steakholder can start the ost-agent npm package, pour compute and a goal into it, and trust it to efficiently map out the path to accomplishing the goal" and `type: Metric` — a type the schema does not define, which made the node and its 8 links invisible to `ost_read_tree`. Restored here as the umbrella Opportunity its body describes; the operator's goal sentence is preserved verbatim above as the record of what they were reaching for._
