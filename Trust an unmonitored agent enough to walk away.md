---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-22-design-goals.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Can't tell if the generated tree is actually any good]]
[[Connecting my systems of record could leak or corrupt them]]
[[Fear the agent could take a destructive, irreversible action]]
[[Want proof no hijackable capability even exists]]
[[Worry the agent is grading its own homework]]
[[A quoted justification makes me check the agent's advice less]]
[[A tool call I got slightly wrong destroyed the note I was filing]]
[[I cannot see what the agent did while I was away, so walking away is a leap]]
[[The agent can't earn wider autonomy, because it has no way to let reality judge its own claims]]
[[My unattended runs recover from tool errors and retries I never find out about]]

**Customer need (operator's perspective):** "I want to download the tool, run one command, then walk away and trust it to run completely unmonitored — and come back to a tree that faithfully reflects what my business is learning, with fresh candidate solutions and assumptions, and nothing unproven dressed up as proven."

The core pain is the leap of faith required to leave an autonomous agent running against real business knowledge with no one watching. Operators will only walk away if they trust both that nothing bad can happen *and* that what they come back to is honest and useful.

**Litmus (more than one way to address?):** Yes — trust can be earned through safety guarantees, faithful-representation guarantees, honesty about validation state, unattended reliability, transparency/audit trails, etc. This is a genuine need, not a solution.

This is an umbrella trust opportunity. Its more specific facets are nested beneath it as child opportunities.

_Provenance: INBOX:2026-07-22-design-goals.md (README + design spec, 2026-07-22). Distilled by autonomous OST pass; unvalidated — for human review._

_Ported from the ost-agent-vault tree (2026-07-24 consolidation). In that vault this node carried the human-authored title "Any steakholder can start the ost-agent npm package, pour compute and a goal into it, and trust it to efficiently map out the path to accomplishing the goal" and `type: Metric` — a type the schema does not define, which made the node and its 8 links invisible to `ost_read_tree`. Restored here as the umbrella Opportunity its body describes; the operator's goal sentence is preserved verbatim above as the record of what they were reaching for._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Append-only audit trail the operator can replay" — re-parented under "I cannot see what the agent did while I was away, so walking away is a leap" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Guided dry-run mode before unattended operation" — re-parented under "I cannot see what the agent did while I was away, so walking away is a leap" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Weekly what-changed-and-why digest" — re-parented under "I cannot see what the agent did while I was away, so walking away is a leap" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "The log is the agent an event-sourced graph the whole tree is projected from" — re-parented under "I cannot see what the agent did while I was away, so walking away is a leap" — this solution answers that need, not the categories beside it

## Issues
- 2026-07-25 Sequenced-after-demand (2026-07-24 review): 41 nodes (~28% of the tree) harden trust for operators who do not yet exist while the outcome's bottleneck is external demand evidence. Hold new growth here until external returning operators > 0. See root Prioritization.
- 2026-08-16 New first-party evidence bearing on this branch's 2026-07-25 growth hold, mapped 2026-08-15 rather than expanded into a new node (holding the hold, not overriding it): `INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md` reports an attended audit found both discovery and build loops execute their automation scripts directly from whatever branch is checked out in a single shared working directory with no worktree isolation, and observed the stuck-branch case sat checked out for that solution's whole stuck period so every firing of both loops ran from an unreviewed branch rather than main until a human manually reset it. The audit's own framing: "nothing currently stops a future build session from editing examples/automation/build-pass.sh itself, leaving that branch checked out, and having that edited script become the executable policy for every subsequent firing of both loops with no review in between." Evidence class for the mechanism observed (branch drift itself): observed. For the risk (unreviewed script becoming policy): inferred, not yet observed. This is concrete, first-party, non-speculative evidence of exactly the kind the growth hold was waiting on external demand to justify spending on — but it is a safety/integrity finding, not a demand signal, so whether it should lift the hold or be treated as a standing exception to it is a human's call. Flagged rather than acted on; no new Opportunity or Solution node created under this held branch.
