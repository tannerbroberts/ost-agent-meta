---
type: Opportunity
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
---
#Opportunity #ported-from-ost-agent-vault #evidence/assertion
[[Golden-set evaluation harness]]
[[Human review sampling with a faithfulness rubric]]
[[Independent LLM judge scores faithfulness to evidence]]

**Customer need (operator's perspective):** "I can't currently tell whether the agent actually produces a good, faithful Opportunity Solution Tree from my real evidence — or whether it's just shuffling nodes around. The plumbing may be well-tested, but I have no signal on whether the *ideation* is any good. I need a way to know it works before I rely on it."

The pain is an inability to judge output quality/efficacy holistically. Moving nodes proves the pipeline runs; it does not prove the discovery reasoning is faithful or valuable. Without that signal, operators can't trust the tool with real decisions.

**Litmus (more than one way to address?):** Yes — golden-set/eval harnesses, independent judge scoring, human review sampling, faithfulness metrics, benchmark trees, etc.

_Provenance: INBOX:2026-07-22-efficacy-critique.md (design review conversation, 2026-07-22). Note: originates as an internal maintainer critique; reframed to the equivalent operator need to trust output quality. Unvalidated — for human review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
