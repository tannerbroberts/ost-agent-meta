---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A digest arriving where stakeholders already read gets read]]

After each pass, send a short digest to wherever the stakeholder already reads things — what changed, what it means for the outcome, and the one or two decisions or tests the agent needs from a human. No new place to visit.

**How it differs from its siblings:** push, not pull. It is the only sibling that works when the stakeholder never remembers to check, and the only one that can pull a human back in when the agent is blocked.

**Trade-off:** a digest nobody asked for becomes noise fast; frequency and ruthless brevity decide whether it is read.

**Riskiest assumptions to test:** that stakeholders open and act on it after the novelty passes (desirability); that a pass's changes can be compressed into a few lines without losing the point (feasibility).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Three-week digest engagement run" — moved under "A digest arriving where stakeholders already read gets read" — the belief this test measures now has a node of its own

## Issues
- 2026-07-25 Cross-branch duplicate (2026-07-24 review): near-identical to 'Weekly what-changed-and-why digest'. See that node's annotation.

## Definition of done

"Three-week digest engagement run"

```
npx vitest run test/adapters/digest-delivery.test.ts
```

Green means: the digest arrives — produced on cadence, pushed to the configured channel rather than left in the vault, naming what changed since the last one rather than restating the tree, and a missed cadence reported as a miss instead of passing silently. Green does **not** measure engagement; what stakeholders do with it needs three weeks and real people.
