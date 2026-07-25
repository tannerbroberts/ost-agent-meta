---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-24-opp-idempotent-runtime.md'
created: '2026-07-24'
---
#Solution #unvalidated #evidence/assertion
[[Kill-at-random-points restart test]]

Every process step records its intent and its completion in an append-only journal, and every write is atomic. A restart replays the journal, skips what already completed, and resumes — no locks to get stuck, no half-written state, killing the process at any instant is safe.

**How it differs from its siblings:** makes interruption *harmless* rather than making it *rare*. It is the only sibling that addresses corruption; the others address availability and drift.

**Trade-off:** every process must be written to be replay-safe, which constrains how future work is built and is easy to violate silently.

**Riskiest assumptions to test:** that all current processes can be made idempotent without major rework (feasibility); that a kill-at-any-point test actually leaves the vault consistent (feasibility); that stakeholders' worry is about corruption at all rather than about drift (desirability).

Status: agent-originated candidate; mechanism was founder-suggested. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Supporting evidence — observed friction (2026-07-24)

`INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md`: a builder pass was backgrounded mid-work; the next pass had no way to tell finished from abandoned. Exactly the failure this solution exists to prevent — first observed instance in the wild. Evidence class: observed behavior (self-reported by the agent at the moment of friction).
