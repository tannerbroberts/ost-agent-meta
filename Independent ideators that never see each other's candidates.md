---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Blind parallel ideators produce more distinct candidates than one agent asked for three]]

Generate candidates in parallel from separate contexts, each blind to the others, and merge only afterwards. Removes the anchoring that makes candidates two and three variations on candidate one — the founder's "context object is SO INFURIATINGLY BAD" complaint applied directly to ideation.

**Contrast with siblings:** Structural rather than prompt-level, and the only option that attacks anchoring at its cause; costs N times the generation budget and can produce near-duplicates by coincidence. "Forced-variation" is far cheaper but relies on naming the right dimension in advance; "Outside-in" is the only one that can introduce information not already in the system.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Do blind parallel ideators produce more distinct candidates than one agent asked for three]] — moved under [[Blind parallel ideators produce more distinct candidates than one agent asked for three]] — the belief this test measures now has a node of its own

## Definition of done

[[Do blind parallel ideators produce more distinct candidates than one agent asked for three]]

```
npx vitest run test/eval/blind-ideator-isolation.test.ts
```

Green means: no ideator's prompt contains a sibling's candidate text, so the blindness this solution is named for actually holds. Green does **not** mean the blind set is more distinct — the test's threshold puts that in front of a human blind-rating shuffled sets on three opportunities, and it stays there.
