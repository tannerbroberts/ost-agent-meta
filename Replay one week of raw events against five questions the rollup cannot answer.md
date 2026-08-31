---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/telemetry/raw-event-question-coverage.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test:** That raw retention answers questions summaries cannot — i.e. that the extra fidelity is *used*, not merely hoarded.

**Design:** Write down five questions before looking at any data. Attempt each against the existing summaries, then against one week of raw events. **Pre-committed threshold:** at least three of five are answerable from raw and not from the rollup. Below that, the fidelity is not paying for itself yet and the cheaper option wins.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-04 instrument: (none) → npx vitest run test/telemetry/raw-event-question-coverage.test.ts — Asserts a week of raw events answers the five named questions and that the derived rollup alone does not, which is the case for storing raw first; fails today because only rollups are retained.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/telemetry/raw-event-question-coverage.test.ts` — No test files found, exiting with code 1
- 2026-08-31 **green** (exit 0) `npx vitest run test/telemetry/raw-event-question-coverage.test.ts` — Duration  312ms (transform 28ms, setup 0ms, collect 32ms, tests 34ms, environment 0ms, prepare 25ms)
