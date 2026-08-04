---
type: Solution
status: unvalidated
source: 'agent-ideated:2026-08-02-maintenance-pass-3'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Time the resource questions once and count answers the vault could not already recover]]

A short, bounded set of resource questions is put to the operator on a schedule rather than once, and every answer carries an expiry date after which the planner stops consulting it and reports the field as unknown. Resources are treated as perishable facts, because they are: a round closes, a token plan changes, a person's appetite for talking to strangers moves.

**Mechanism:** periodic elicitation with decay. The distinguishing property is not the asking — it is that a stale answer degrades to "unknown" instead of quietly staying authoritative.

**What it targets that the other two cannot:** the failure mode where a manifest filled in confidently on day one is still steering plans in week six. This vault has a live instance of exactly that shape recorded on [[Every run ends blocked on a credential only I hold]] — a blocker asserted once from a true observation, carried verbatim through eight briefings, growing more confident each restatement and less examined, until a pass finally re-derived it and found the framing wrong.

**Blind spots:** it spends human minutes, which is the resource this operator has already declared they do not have, and every ask is an escalation — the thing [[I need the tree's output to be actionable by compute alone, because my hours don't exist]] exists to reduce. Cadence set too loose and it is a manifest with extra steps; set too tight and it is a nag that gets ignored, which is worse than not asking, because unanswered-and-expired looks identical to never-asked.

**Compare against** [[A declared resource manifest the planner must cite before it ranks anything]] **and** [[Constraint profile mined from what actually blocked the loop]].

## Definition of done

[[Time the resource questions once and count answers the vault could not already recover]]

```
npx vitest run test/config/resource-question-recoverability.test.ts
```

Green means each standing resource question is labelled by whether the vault can already recover its answer — which is the count that decides whether asking on a cadence buys anything, or just bills the operator for what is already on disk. It does not settle the timing half of the question: how fast an answer goes stale is a property of the operator's world, not of the vault.
