---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-opp-transcript-ingestion.md'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A session transcript contains distillable stalls and dead ends worth the next pass's attention]]

After each run, read the agent's own chat transcript, distil the questions, uncertainties, stalls and dead ends it hit, and drop them into the inbox as evidence for the next pass.

**How it differs from its siblings:** retrospective and complete — it sees the whole session including things the agent never recognised as friction, because a second reader interprets the record rather than the agent self-reporting in the moment.

**Trade-off:** transcripts are large, noisy, and may contain content that shouldn't be committed to a shared vault; and a summariser reading its own species' output may flatter it.

**Riskiest assumptions to test:** that transcripts contain friction a human agrees is real product evidence (desirability); that distillation produces a handful of useful items rather than dozens of restatements (feasibility).

Status: agent-originated candidate; mechanism was founder-suggested. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Hand-distil three past sessions" — moved under "A session transcript contains distillable stalls and dead ends worth the next pass's attention" — the belief this test measures now has a node of its own

## Build + first-run evidence (2026-07-24)

`INBOX:2026-07-24-builder-transcript-harvester-shipped.md`: this solution was BUILT by the builder loop (src/adapters/transcript.ts, 19 tests, enabled on this vault) — and its first live harvest of one session yielded exactly 1 friction event (tool_error ×1), i.e., a thin first signal (`TRANSCRIPT:8fc8d6e3-...`). Note the layer tension: a built-and-running solution still carries status: unvalidated here because no human has judged whether its output is worth anything — the build note is evidence of feasibility, not desirability. Its assumption test (Hand-distil three past sessions) remains the arbiter and remains unrun.

## Issues
- 2026-08-05 Deliberately not instrumented by the 2026-08-05 unattended pass, and the reason is worth recording because it is the good kind of problem. Unlike most solutions in this bucket, the mechanism here appears to have shipped: the transcript channel is live and reported by `ost_ingest_inbox`, and this pass read fifteen harvested session records covering 2026-07-24 through 2026-08-05. A spec asserting "the harvester produces a record per session" would therefore be green on arrival, and a command that cannot fail measures nothing. Its test — "Hand-distil three past sessions" — is the comparison half, a human distilling the same sessions by hand and checking what the harvester missed, and that stays with a person. Two things a human should settle. First, whether the test is effectively answered by the shipped harvester and should be closed with `ost-agent result` rather than left open since 2026-07-24. Second, the one claim that may still be red: `ost_ingest_inbox` reports "[transcript] 0 new" without saying how many sessions it considered, so a session it silently skipped and a window with genuinely nothing in it produce the same line. If per-session coverage — every session in the window either harvested or explicitly named as skipped, with a reason — is part of what this solution promises, that is instrumentable and would fail today. This pass could not distinguish "no sessions" from "sessions passed over" without reading the repository, which it holds no grant to do.
