---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[An operator will adopt an outside-sourced candidate into their real consideration set]]

Seed the candidate set from outside the system — how other products, other industries, or plainly non-software processes have addressed the same underlying need — and only then generate natively. The set starts wider than anything the current context could have produced from itself.

**Contrast with siblings:** The only option that introduces genuinely new information rather than rearranging what is already present, which is exactly what the other two cannot do; in exchange it depends on an outside channel, and imported candidates carry a transfer risk that native ones do not.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Would an operator adopt an outside-sourced candidate into their consideration set]] — moved under [[An operator will adopt an outside-sourced candidate into their real consideration set]] — the belief this test measures now has a node of its own

## Definition of done

[[Would an operator adopt an outside-sourced candidate into their consideration set]]

```
npx vitest run test/web/outside-in-candidate-provenance.test.ts
```

Green means: the operator is never asked to judge an idea whose origin the tree cannot name — every outside-in candidate records its host as `WEB:<host>`, enters at the `assertion` floor whatever that host's standing, and one created without a retrievable source is refused. Green does **not** mean an operator would adopt it; that is their decision.
