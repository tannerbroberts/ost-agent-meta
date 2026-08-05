---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A locked outcome addresses what operators are actually afraid of when they leave it running]]
[[Drift is auditable after the fact from the pass records alone]]

The outcome is a locked contract: no autonomous process can alter it, any proposed change is raised as a visible question for a human, and every pass records which goal it ran against so drift is auditable after the fact.

**How it differs from its siblings:** addresses the second half of the trust worry — not "will it stop?" but "will it still be pointed where I left it?". Availability and crash-safety do nothing for this.

**Trade-off:** a locked goal that turns out to be mis-formed keeps compounding effort in the wrong direction; the escape hatch has to be easy for a human and impossible for the agent.

**Riskiest assumptions to test:** that goal drift is a real fear rather than a hypothetical one (desirability); that agents reliably raise rather than reinterpret an ill-fitting goal (feasibility).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Unprompted-fear interviews about leaving it running" — moved under "A locked outcome addresses what operators are actually afraid of when they leave it running" — the belief this test measures now has a node of its own
- 2026-08-05 unlinked "Every pass records the outcome text it ran against, and a changed outcome is visible as a change" — moved under "Drift is auditable after the fact from the pass records alone" — the belief this test measures now has a node of its own

## Definition of done

"Every pass records the outcome text it ran against, and a changed outcome is visible as a change"

```
npx vitest run test/loop/goal-contract-recorded.test.ts
```

Two of this node's three clauses already hold and are not what the command measures. *No autonomous process can alter the outcome* is enforced by construction — an Outcome cannot be created or set through any tool an agent holds — and *raise the change as a visible question* is the only move an agent has anyway. A spec for either would pass on arrival.

Green means the third clause is real: every pass records the outcome text it ran against, two passes that ran against different texts are distinguishable from their records alone, and a mid-run change is reported rather than stamped as though one end of it had held throughout. The gap is easy to miss because the current outcome is always readable — what is never recoverable is what a *given pass* ran against, which is the only thing that makes drift auditable after the fact.

It settles neither of this node's stated riskiest assumptions. Whether goal drift is a real fear is "Unprompted-fear interviews about leaving it running". Whether an agent reliably raises rather than quietly reinterprets an ill-fitting goal is reached by nothing in this tree — an agent can record the exact text it ran against, honestly, and still have read it to mean something the human did not intend, and a perfect audit trail of a reinterpretation is still a reinterpretation.
