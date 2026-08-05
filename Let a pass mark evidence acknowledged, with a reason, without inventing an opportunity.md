---
type: Solution
status: unvalidated
source: >-
  agent-ideation — mapped-ledger dead-end observed in this vault and
  RUNTIME:tetrix-ost@2328e61
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A pass's decision not to distil an opportunity is a judgement worth recording]]

**The idea.** A tool call that records "this evidence has been dealt with, and here is what I did with it" — including the case where what the agent did was decline to distil an opportunity from it, and say why. The ledger stops being a proxy for "an Opportunity node cites this source" and starts recording an actual judgement.

**Why the current design forces a bad choice.** Today the mapped set is only written by the batch `P2_map` runner; a session-driven pass has no way to touch it, so `done: true` is unreachable no matter how good the pass was. That is the mechanical half. The semantic half is worse: because being mapped is inferred from a node carrying the evidence's `source`, the only way for an agent to clear an item is to *create a node citing it*. When the honest answer is "this evidence contains no unmet customer need," the tool surface offers exactly two moves — invent a need that the evidence does not support, or accept a permanent false alarm.

The tetrix instance faced this precisely and chose correctly. Its evidence item recorded already-built, de-risked capability. It declined to fabricate an opportunity, appended the content to the Outcome as discovery context where it usefully constrains ideation, and wrote a paragraph explaining that the item would be reported outstanding forever. **The system's incentives pointed at confabulation and the agent walked the other way.** Nothing in the design made that happen — it was a good agent covering for a bad affordance, and that is not something to rely on. A less careful pass invents the opportunity, and now the tree contains a need no customer has.

**What the affordance has to carry.** A disposition and a reason, both auditable: *distilled into opportunity X*, *recorded as context on node Y*, *declined — no unmet need present*, *deferred — needs a human*. A bare "mark mapped" boolean would fix termination and lose the reasoning, which is the part that makes the tree trustworthy. The disposition also gives a human reviewer a cheap audit: every declined item is a place to check whether the agent was being careful or lazy, and there should be few enough of them to read.

**Interaction with the append-only boundary.** Both instances refused to hand-edit `mapped.json` from the shell, correctly, to preserve the tools-only trust boundary. That refusal is a feature and this solution must not undermine it: the disposition should be written through the tool surface and land in the audit trail like every other change.

⚠️ Unvalidated. Proposed by an agent, from two instances' observed behaviour.

## History
- 2026-07-24 provenance repaired: frontmatter source was corrupted to ">-" by the 57c3745 vault merge; restored from the body's provenance footnote (human-authorized repair).
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Blind-review a pass's acknowledge-or-map calls on the seven stranded items]] — moved under [[A pass's decision not to distil an opportunity is a judgement worth recording]] — the belief this test measures now has a node of its own

## Definition of done

[[Blind-review a pass's acknowledge-or-map calls on the seven stranded items]]

```
npx vitest run test/ost/evidence-acknowledge.test.ts
```

Green means: the verb exists and cannot be abused as a silent dismissal — acknowledging records a reason and the node the item was filed under, takes it off `unmappedEvidence`, and is refused with no reason given. Green does **not** mean the acknowledgements were honest; whether a pass filed or dodged is a blind human review and stays with a human.

The 2026-08-05 pass is the strongest argument yet for this solution: it found all eighteen stranded items already cited by name in existing Opportunity bodies, and still could not clear one of them, because the only tool for it was to create eighteen near-duplicate nodes.
