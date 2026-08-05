---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A kill criterion written when a candidate was cheap actually gets honoured when it is expensive]]

Every candidate records, at creation, the observation that would end it — before anyone is attached to it. Killing then becomes bookkeeping against a commitment made when it was cheap, rather than an argument had when it is expensive.

**Contrast with siblings:** Cheapest and the only one that acts *before* effort accrues; but a criterion written at birth may be the wrong one by the time evidence arrives. "Cheapest-disconfirmer first" optimises the order of testing; "Candidate tournament" needs no criterion at all because candidates are judged relative to each other.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Do candidates carrying kill criteria actually get killed within two weeks" — moved under "A kill criterion written when a candidate was cheap actually gets honoured when it is expensive" — the belief this test measures now has a node of its own

## Definition of done

"Do candidates carrying kill criteria actually get killed within two weeks"

```
npx vitest run test/ost/kill-criteria-required.test.ts
```

Green means: the criteria exist and are evaluable — a Solution cannot be created without a condition and a date, both stored as fields rather than buried in prose, and the sweep lists every candidate whose date has passed with its condition unmet. Green does **not** mean anything gets killed. That needs two weeks to elapse and a human willing to act on the list, and it is the half that decides whether this solution does any good.
