---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/telemetry/export-requires-consent.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test:** That operators will hand over raw, un-redacted usage when asked plainly — the desirability risk that decides whether any raw channel has a population at all.

**Design:** Offer the export to the first ten operators with an honest description of exactly what leaves their machine. **Pre-committed threshold:** at least four of ten consent without requiring a bespoke redaction feature. Below that, consent is the bottleneck, not the pipe, and effort should move to redaction rather than throughput.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/telemetry/export-requires-consent.test.ts — Asking whether operators consent is only safe once consent is the thing that gates the shipping, and nothing today enforces that. This asserts the mechanism the question depends on: the event log is written locally by default with no outward path, raw export is refused unless a dated consent record exists in the vault, and revoking consent stops further export without deleting what the operator already holds. Missing-spec red, not assertion red — no consent record or export gate exists, so the command fails on a missing file; a builder should write it against the real telemetry writer so it goes red on an export that proceeds without consent. It does not settle whether operators WILL consent — that is a person's decision about their own data, and no exit code substitutes for asking them.
