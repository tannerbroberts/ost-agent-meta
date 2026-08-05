---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators will consent to shipping raw usage out of their own vault]]

Raw events accumulate inside the operator's own vault, under their own git history, and travel outward only on an explicit consented export. The product's default posture stays local-first; the founder receives full fidelity from those who opt in rather than thin telemetry from everyone.

**Contrast with siblings:** Lowest trust cost and the only option compatible with operators who will never point their work at someone else's server; in exchange the sample is self-selected and probably small. "Raw-first store" assumes collection is allowed; this one assumes it must be earned.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Will operators consent to shipping raw usage from their own vault]] — moved under [[Operators will consent to shipping raw usage out of their own vault]] — the belief this test measures now has a node of its own

## Definition of done

[[Will operators consent to shipping raw usage from their own vault]]

```
npx vitest run test/telemetry/export-requires-consent.test.ts
```

Green means: consent is load-bearing, not a promise — the log is local by default with no outward path, raw export is refused without a dated consent record, and revoking consent stops further export without touching what the operator already holds. Green does **not** mean operators will consent; that is their decision about their own data, and it has to be asked.
