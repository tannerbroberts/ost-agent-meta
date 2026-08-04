---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/adapters/ingest-backpressure-provenance.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test:** That the channel can absorb a realistic burst without losing events or detaching them from their source.

**Design:** Replay a synthetic burst at 10× the highest observed rate. **Pre-committed threshold:** zero events lost, 100% still carrying a resolvable source id, and recovery to real-time within ten minutes of the burst ending. Any silent loss fails the test outright — a channel that drops without saying so is the failure mode this solution exists to prevent.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/adapters/ingest-backpressure-provenance.test.ts — Observed peak is already recorded in the usage traces, so the spec can synthesise ten times that volume, drive it through the ingest channel, and assert every captured record still carries the source id and timestamp it arrived with and that no item is dropped or double-captured; it fails today because the channel has no backpressure path and the assertion has nothing to exercise.
