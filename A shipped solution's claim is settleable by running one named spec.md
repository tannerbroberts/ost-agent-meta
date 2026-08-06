---
type: Assumption
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Require a shipped solution to be asked for an observation and not for a red command]]

**The belief, stated so it could be false.** For a solution recorded as shipped, there exists one command in the repository's own suite whose green exit code is meaningful evidence that the claimed mechanism is present — enough to move the node off `assertion`.

**Kind.** Feasibility.

**How it could turn out false.** A green spec proves that some code path behaves as the spec asserts, and the spec is written by the same party that wrote the claim. On "Refuse a wiki-link that contains a newline" the shipped mechanism is `wrappedLinkTargets` with three callers — a spec could assert the rule fires and pass while one of the three callers had quietly stopped using it, which is the exact failure that node's own history says the product is prone to. If the spec is written from the node's prose rather than from the mechanism, a green run certifies the prose against itself and the rung it earns is unearned.

**Why it is the riskiest one here.** The whole appeal of this solution over its cheaper sibling is that it collects evidence rather than just silencing noise. If the evidence it collects is circular, the sibling is strictly better and this one is a second queue bought for nothing.
