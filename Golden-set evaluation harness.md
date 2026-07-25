---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does the golden set discriminate good trees from bad]]

**Candidate solution (unvalidated).** Curate fixtures of real evidence paired with expert-reviewed "good" trees, and score each agent run against them (coverage, faithfulness, no-solution-as-opportunity, etc.). Efficacy becomes a measured regression signal rather than an assumption. Unlike the existing scripted end-to-end test (canned outputs prove only that nodes move), this tests whether the *ideation* is any good.

**Approach:** *benchmark against ground truth*.

**Contrast with siblings:** unlike the LLM judge (scalable, no fixtures) this needs curated data but gives a stable regression baseline; unlike human sampling it runs automatically every build.

_Addresses: "Can't tell if the generated tree is actually any good". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
