---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Resumable append-only process journal]]
[[Supervisor heartbeat with automatic restart]]
[[Immutable goal contract]]

An unattended run has no supervisor and no resumable record. If it fails at hour two, hours three through eight are silence, and what it had finished by then has to be reconstructed afterwards from whatever it happened to write.

## Evidence — a backgrounded session hit this directly (mapped 2026-08-15)

`INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` (filed by builder-loop, kind: blocked): "An earlier builder pass was backgrounded mid-work; the next pass had no way to tell what it had finished versus abandoned." Same need as this node's own prose — a run interrupted (backgrounded, not just crashed) leaves no trustworthy marker of where it stopped — reused here rather than filed as a new sibling. Evidence class: observed behavior, self-reported by the agent that hit it; grounds usability, not demand.

## Corroborating evidence — 2026-08-16
`INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` — a builder pass was backgrounded mid-work; the next pass had no way to tell what it had finished versus abandoned. Same need as this node, filed from the build loop's own friction rather than an interview. Evidence class: observed (self-reported by the agent) — grounds usability, not demand.

## Corroborating evidence
- INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md — builder-loop self-filed friction (blocked): an earlier builder pass was backgrounded mid-work; the next pass had no way to tell what it had finished versus abandoned. Same need as this node, filed from the build side rather than the operator side.

## Corroboration — a builder pass filed this as its own blocker (unattended sweep, 2026-08-17)

`INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` (filed by `builder-loop`, 2026-07-24): an earlier builder pass was backgrounded mid-work, and the next pass had no way to tell what it had finished versus abandoned. Same need this node already states, filed from the build side rather than the maintenance side: the process that died left no marker of where it stopped, so the next firing could not pick up cleanly.

_Source: `INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md` — observed behaviour, self-reported by the product's own agent at the moment of friction. Grounds usability, not demand. Corroboration only; the node's rung is unchanged._
