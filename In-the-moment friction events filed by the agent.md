---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An agent given a one-line channel at the point of pain will actually file]]

Give the agent a way to file a small structured note the moment it is blocked, uncertain about a rule, or forced to guess — one line, at the point of pain, while the context is still live.

**How it differs from its siblings:** captured at the moment of friction with full context, and cheap enough to run always. It only catches friction the agent *notices*, where the harvester catches friction it doesn't.

**Trade-off:** self-reporting is biased and easy to skip under load; needs a habit or a hook to be reliable.

**Riskiest assumptions to test:** that the agent reliably files events rather than pushing through silently (feasibility); that a one-line note carries enough context to be actionable later (usability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Five-pass count of self-filed friction events" — moved under "An agent given a one-line channel at the point of pain will actually file" — the belief this test measures now has a node of its own

## Definition of done

"Five-pass count of self-filed friction events"

```
npx vitest run test/telemetry/self-filed-friction-events.test.ts
```

Green means: two of the test's three clauses hold — at least one self-filed event per pass across five recorded passes, and every event carries the tool, the failing input, and what was expected, so bare prose fails. Green does **not** cover the third clause. The unfiled-to-filed ratio below 2:1 requires counting friction that left no record, which only a human reading the same five transcripts can do — and that is precisely the clause that decides whether self-reporting can stand alone.
