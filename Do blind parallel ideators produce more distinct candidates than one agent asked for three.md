---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/eval/blind-ideator-isolation.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test:** That anchoring — not model capability — is what makes candidate sets narrow.

**Design:** Same opportunity, both methods, candidates shuffled and rated for pairwise distinctness by a human who does not know which method produced which. **Pre-committed threshold:** the blind set is rated more distinct on at least two of three opportunities. If not, the ceiling is capability and the extra generation budget is wasted.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/blind-ideator-isolation.test.ts — The test's own premise is that anchoring, not capability, narrows candidate sets — which presumes the ideators are genuinely blind to each other. This asserts exactly that and nothing more: each parallel ideator's assembled prompt contains none of its siblings' candidate text, and a run configured as blind that leaks a sibling candidate into a prompt fails. Missing-spec red, not assertion red — blind parallel ideation is not built, so the command fails on a missing file; a builder should write it against the real prompt-assembly path so it goes red on the leak rather than on absence. It does not settle whether the blind set is MORE DISTINCT: the test's threshold puts that in front of a human blind-rating shuffled sets, and it stays there.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/eval/blind-ideator-isolation.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/eval/blind-ideator-isolation.test.ts` — Duration  1.28s (transform 160ms, setup 0ms, collect 240ms, tests 814ms, environment 0ms, prepare 29ms)
