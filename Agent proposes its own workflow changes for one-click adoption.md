---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The changes an agent drafts for its own ruleset are ones a human would accept]]

When the agent hits the same friction repeatedly, it drafts the change to its own ruleset as a reviewable proposal — with the friction evidence attached — that a human accepts or rejects in one action. The agent keeps running the old workflow until then.

**How it differs from its siblings:** shifts the *authoring* cost rather than the interruption cost, and closes the loop with the friction-evidence channel. Adoption remains a human decision, so it never surprises the operator.

**Trade-off:** improvements move only as fast as the human reviews them; if nobody reviews, nothing improves and proposals pile up.

**Riskiest assumptions to test:** that the agent's self-proposed changes are ones a human would accept (desirability); that reviewing a proposal is genuinely cheaper than writing the change (usability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Acceptance rate of five self-drafted ruleset changes]] — moved under [[The changes an agent drafts for its own ruleset are ones a human would accept]] — the belief this test measures now has a node of its own

## Definition of done

[[Acceptance rate of five self-drafted ruleset changes]]

`npx vitest run test/knowledge/ruleset-proposal.test.ts`

The spec asserts the property that makes this candidate safe rather than merely clever: a pending proposal does **not** alter the ruleset the pass executes — the agent keeps running the old workflow until a human accepts — and every proposal carries the friction evidence ids that triggered it, so adoption is a decision made against evidence rather than against prose. Red today because the ruleset is generated from source and the agent has no way to draft a change to it.

**What a green here does not settle.** Both riskiest assumptions the node names. Whether the agent's self-proposed changes are ones a human would accept is desirability, and whether reviewing a proposal is genuinely cheaper than writing the change is usability — a spec sees neither. Nor does it touch the stated trade-off: if nobody reviews, nothing improves and proposals pile up, and a passing suite would be perfectly compatible with a queue of fifty unread drafts.
