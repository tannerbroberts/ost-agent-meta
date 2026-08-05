---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/knowledge/forced-variation-prompt.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test:** That forcing variation does not simply buy diversity with plausibility — the obvious failure is three genuinely different and three genuinely useless candidates.

**Design:** Blind-rate constrained and unconstrained sets on both distinctness and plausibility. **Pre-committed threshold:** distinctness up, and mean plausibility down by no more than 10%. A larger quality drop means the constraint is producing noise, not range.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/knowledge/forced-variation-prompt.test.ts — The threshold compares constrained against unconstrained sets, which presumes the constraint reaches the model at all. This asserts that half: an ideation prompt built for a target opportunity names an explicit variation dimension and names a different one for each sibling candidate requested, and a prompt built with the constraint enabled that omits the dimension fails. Missing-spec red, not assertion red — forced-variation prompting is not built, so the command fails on a missing file; a builder should write it against the real prompt builder in src/knowledge so it goes red on the missing dimension instead. It settles neither half of the actual threshold: distinctness up and plausibility down by no more than 10% both require a human blind-rating the two sets, and both stay with a human.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/knowledge/forced-variation-prompt.test.ts` — No test files found, exiting with code 1
