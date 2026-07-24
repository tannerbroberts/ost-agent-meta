---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-opp-idempotent-runtime.md'
created: '2026-07-24'
---
#Solution #unvalidated
[[Kill-at-random-points restart test]]

Every process step records its intent and its completion in an append-only journal, and every write is atomic. A restart replays the journal, skips what already completed, and resumes — no locks to get stuck, no half-written state, killing the process at any instant is safe.

**How it differs from its siblings:** makes interruption *harmless* rather than making it *rare*. It is the only sibling that addresses corruption; the others address availability and drift.

**Trade-off:** every process must be written to be replay-safe, which constrains how future work is built and is easy to violate silently.

**Riskiest assumptions to test:** that all current processes can be made idempotent without major rework (feasibility); that a kill-at-any-point test actually leaves the vault consistent (feasibility); that stakeholders' worry is about corruption at all rather than about drift (desirability).

Status: agent-originated candidate; mechanism was founder-suggested. Unvalidated.
