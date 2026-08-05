---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
---
#Solution #unvalidated #evidence/assertion
[[Does a named-dimension constraint raise distinctness without lowering candidate quality]]

Require each candidate in a set to differ from its siblings along a declared dimension — who does the work, what is automated versus manual, what is bought versus built, what is deliberately given up. Distinctness becomes a stated property of the set rather than something hoped for.

**Contrast with siblings:** Nearly free and immediately auditable, since the dimension is written down; but it can only spread candidates across dimensions someone thought to name, so it widens the search inside the existing frame rather than escaping it.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Definition of done

[[Does a named-dimension constraint raise distinctness without lowering candidate quality]]

```
npx vitest run test/knowledge/forced-variation-prompt.test.ts
```

Green means: the constraint actually reaches the model — every candidate requested carries an explicit and distinct variation dimension in its prompt. Green does **not** mean the constraint works: distinctness up, and plausibility down by no more than 10%, both need a human blind-rating the two sets.
