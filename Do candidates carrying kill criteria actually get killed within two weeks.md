---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/ost/kill-criteria-required.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test:** That a written criterion is actually honoured — the failure mode is a tree full of unmet kill conditions that everyone reads past.

**Design:** Attach criteria to ten candidates and revisit after two weeks. **Pre-committed threshold:** at least three are retired, and no candidate whose criterion was demonstrably met is still live. A single survivor with a met criterion fails the test — that is the exact behaviour this solution exists to prevent.

*Proposed only. A human runs this.*

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/ost/kill-criteria-required.test.ts — Nothing can be killed by criteria that were never written down, and no node carries any — which is why "Nothing kills a candidate, so every idea I have ever had is still alive" is a live opportunity with 264 solutions under the tree. This asserts the birth half: creating a Solution is refused without kill criteria naming a condition and a date, the criteria are stored as fields rather than prose so they can be evaluated, and the sweep lists every candidate whose date has passed with its condition unmet. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file is absent; a builder should write it against the real create path so it goes red on a criteria-free Solution that today succeeds. It does not settle whether anything actually GETS killed — that needs two weeks to elapse and a human willing to act on the list.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/kill-criteria-required.test.ts` — No test files found, exiting with code 1
- 2026-08-30 **green** (exit 0) `npx vitest run test/ost/kill-criteria-required.test.ts` — Duration  1.19s (transform 474ms, setup 0ms, collect 780ms, tests 72ms, environment 0ms, prepare 76ms)
