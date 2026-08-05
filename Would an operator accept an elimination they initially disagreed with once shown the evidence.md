---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/eval/tournament-elimination.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test:** That operators will let an automated process remove their ideas — the trust risk that decides whether elimination is ever adopted, independent of whether it is correct.

**Design:** Present five eliminations with their grounding to operators who did not run the tournament, including at least two the operator's stated prior favoured. **Pre-committed threshold:** at least three of five accepted without appeal. Below that, the agent should propose eliminations for confirmation rather than perform them.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/tournament-elimination.test.ts — Asserts the two properties that make this a tournament rather than a ranking: every elimination cites a specific evidence id or recorded result, and no round ever crowns a candidate — the consideration set only shrinks, and declaring a winner stays a human's call. Red today because no tournament exists and nothing enforces that an elimination be grounded.
