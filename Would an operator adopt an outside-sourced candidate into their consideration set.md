---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/web/outside-in-candidate-provenance.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test:** That imported candidates read as relevant rather than as generic advice — if operators discard them on sight, the widening is theoretical.

**Design:** Mix three outside-sourced candidates into an otherwise native set of six, unlabelled, and ask the operator which they would carry forward. **Pre-committed threshold:** at least one outside-sourced candidate is carried forward in two of three trials. Below that, the sourcing needs adaptation to context before it is worth building a channel for.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/web/outside-in-candidate-provenance.test.ts — An operator cannot sensibly adopt or refuse an outside-sourced candidate without seeing where it came from, so provenance is the precondition for the adoption question rather than a detail of it. This asserts it: a candidate drawn from how another product solved the opportunity records the host it came from as `WEB:<host>`, enters at the `assertion` floor regardless of that host's standing, and an outside-in candidate created without a retrievable source is refused — so the operator is never asked to judge an idea whose origin the tree cannot name. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file is absent; a builder should write it against the real ideation path so it goes red on an unsourced outside-in candidate. It does not settle whether an operator would ADOPT one, which is a person's decision and stays with a human.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/web/outside-in-candidate-provenance.test.ts` — No test files found, exiting with code 1
