---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/telemetry/self-filed-friction-events.test.ts
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility):** The agent will actually file friction events under load, rather than pushing through silently and reporting a clean run.

**Proposed test:** Add the instruction and the filing affordance, run five ordinary passes, and count. Separately, have a human read the transcripts of those same five passes and count the friction moments that went unfiled.

**Size:** five passes of normal operation; the comparison is the whole cost.

**Pre-committed threshold:** ≥1 event filed per pass AND ≥70% of the events specific enough for a human to act on AND the unfiled-to-filed ratio below 2:1. A high miss rate means self-reporting is a supplement, not a channel.

**Decides:** whether self-reporting can stand alone or must be paired with retrospective harvesting.

Proposed by the agent — a human performs the transcript comparison; the agent must not score its own reporting rate. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/telemetry/self-filed-friction-events.test.ts — Two of the three clauses in this threshold are countable without a person. This asserts them: across a fixture of five recorded passes the friction channel holds at least one self-filed event per pass, and every filed event carries the fields that make it actionable — the tool, the failing input, and what was expected — so an event filed as bare prose fails. Missing-spec red, not assertion red: the pass cannot read the repo, so the file is absent and the command fails on absence; a builder should write it against the real telemetry writer so it goes red on the missing per-pass floor. It cannot settle the third clause, the unfiled-to-filed ratio below 2:1, because counting what was NEVER filed means reading the transcripts for friction that left no record — the node already assigns that to a human, and it stays there.
