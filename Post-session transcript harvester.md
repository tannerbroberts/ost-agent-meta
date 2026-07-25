---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-24-opp-transcript-ingestion.md'
created: '2026-07-24'
---
#Solution #unvalidated #evidence/assertion
[[Hand-distil three past sessions]]

After each run, read the agent's own chat transcript, distil the questions, uncertainties, stalls and dead ends it hit, and drop them into the inbox as evidence for the next pass.

**How it differs from its siblings:** retrospective and complete — it sees the whole session including things the agent never recognised as friction, because a second reader interprets the record rather than the agent self-reporting in the moment.

**Trade-off:** transcripts are large, noisy, and may contain content that shouldn't be committed to a shared vault; and a summariser reading its own species' output may flatter it.

**Riskiest assumptions to test:** that transcripts contain friction a human agrees is real product evidence (desirability); that distillation produces a handful of useful items rather than dozens of restatements (feasibility).

Status: agent-originated candidate; mechanism was founder-suggested. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Build + first-run evidence (2026-07-24)

`INBOX:2026-07-24-builder-transcript-harvester-shipped.md`: this solution was BUILT by the builder loop (src/adapters/transcript.ts, 19 tests, enabled on this vault) — and its first live harvest of one session yielded exactly 1 friction event (tool_error ×1), i.e., a thin first signal (`TRANSCRIPT:8fc8d6e3-...`). Note the layer tension: a built-and-running solution still carries status: unvalidated here because no human has judged whether its output is worth anything — the build note is evidence of feasibility, not desirability. Its assumption test (Hand-distil three past sessions) remains the arbiter and remains unrun.
