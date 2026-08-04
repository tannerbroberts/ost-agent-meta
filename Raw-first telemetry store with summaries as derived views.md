---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
---
#Solution #unvalidated #evidence/assertion
[[Replay one week of raw events against five questions the rollup cannot answer]]

Keep the full event stream as the system of record and never discard it; every count, rollup and digest becomes a view computed *over* the raw log rather than a substitute for it. New questions get asked of history that has already been collected instead of requiring new instrumentation and a wait.

**Contrast with siblings:** Maximum answerability, maximum storage and privacy exposure. "Operator-owned local event log" trades central answerability for consent; "Backpressure-tolerant ingest" is about surviving the volume this option creates rather than about what is kept.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Definition of done

[[Replay one week of raw events against five questions the rollup cannot answer]]

```
npx vitest run test/telemetry/raw-event-question-coverage.test.ts
```

Green means a week of raw events answers the five named questions and the derived rollup alone does not — the demonstration that summarising first loses something specific, rather than the general worry that it might. It does not settle the cost side: what raw retention takes in storage and in the operator's consent is untouched by this command.
