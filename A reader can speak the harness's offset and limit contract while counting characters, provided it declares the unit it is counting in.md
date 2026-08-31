---
type: Assumption
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-31'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

The candidate assumes the borrowed contract survives the unit mismatch — that a reader counting characters can accept `offset` and `limit` usefully, so long as every response says which unit it is denominated in rather than leaving a caller to assume the harness's tokens.

Stated so it could be false: it is false if an undeclared unit is indistinguishable from a declared one at the point of use. A caller that passes `limit: 25000` meaning tokens and receives 25,000 characters gets roughly a quarter of what it asked for and no signal that anything was reinterpreted — which is worse than today's refusal, because today's refusal at least states the units it enforced.

**A second assumption this candidate rests on, deliberately not written as a node here.** Whether the harness's contract stays stable enough to borrow. That belief is about an outside party's future behaviour, no spec in this repository can reach it, and this tree already records the precedent that makes it sharp — the `SlashCommand` to `Skill` rename that left a deny rule silently inert for four days. A human should add it as a sibling assumption and set its lane; this unattended surface holds no call that can label one, so writing it here would only produce an entry nothing can clear.
