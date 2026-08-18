---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/contribution-estimate.test.ts
---
#AssumptionTest #unvalidated #viability #evidence/assertion

**Assumption under test:** That estimated contribution bears any relationship to realised contribution — otherwise the field is confident-looking noise that makes the map *less* trustworthy.

**Design:** Record estimates for six targets, then wait a month and compare against what the top metric actually did. **Pre-committed threshold:** the estimates rank-order the realised movements better than chance on at least four of six pairs. Failing that, keep the field but render it as an explicitly unreliable guess rather than an input to prioritisation.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/ost/contribution-estimate.test.ts — An estimate cannot survive a month of movement if it was never written down in a form that can later be checked against one. This asserts the recording half: a node carrying a contribution estimate states the local metric, the distant goal it ladders to, and a dated figure, and the rollup surfaces the estimate alongside what actually moved so the two can be compared later; an estimate stored as loose prose with no date or no named goal metric fails. Missing-spec red, not assertion red — no contribution-estimate field exists, so this fails on a missing file; a builder should write it against the real node schema so it goes red on an unstructured estimate. It does not settle whether the estimates SURVIVE — that needs a month of real movement to elapse, which is neither a spec nor a person but simply time, and the comparison is a human's to make when the month is up.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/contribution-estimate.test.ts` — No test files found, exiting with code 1
- 2026-08-18 **green** (exit 0) `npx vitest run test/ost/contribution-estimate.test.ts` — Duration  510ms (transform 183ms, setup 0ms, collect 301ms, tests 18ms, environment 0ms, prepare 29ms)
