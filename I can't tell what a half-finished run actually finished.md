---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

When a run is stopped, backgrounded, or dies mid-work, nothing marks where it got to. The next run — or the operator — cannot tell finished work from abandoned work, so it either redoes, skips, or guesses.

Grounding: a builder pass was backgrounded mid-work on 2026-07-24 and the next pass had no way to tell what it had finished versus abandoned (agent-filed friction, kind: blocked).

Litmus: progress markers/checkpoints, a run journal, idempotent work detection, resumable pass state — multiple distinct ways to address. Distilled by the mapping agent from agent-self-reported observation; unvalidated. Distinct from [[What the agent learns doesn't accumulate over time]] (cross-session knowledge) — this is intra-run work-state.
