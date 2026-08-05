---
type: Solution
source: 'agent-ideated:2026-08-03-unattended-sweep-builder-capability'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Asked at the moment the reasoning is still in their head, a collaborator will deposit it — and come back unasked]]

**The mechanism:** the deposit channel announces itself at the moment the reasoning is still in the collaborator's head. When a session, a PR or a review closes, the collaborator is asked one question in the surface they are already using — no new tool, no separate site, no account — for the reasoning behind what they just did: what they considered and rejected, what they could not do and why, what they would have done with more room. The agent stores the answer verbatim and infers nothing.

**Why this shape.** This is the candidate that takes the opportunity's second facet seriously rather than routing around it: the node's own framing is that people holding the signal *do not know it is welcome as evidence*, which is a problem no amount of inference solves, because the signal was never emitted. It is also the only candidate that can capture the counterfactual — what a builder chose not to attempt is invisible in every artifact and obvious to the person who chose it.

**Chief risk, stated plainly:** it rests entirely on voluntary compliance, and compliance is not randomly distributed. The collaborators whose capability is least legible from artifacts are the ones least likely to sit and write a paragraph, so the profile would be richest exactly where it was already adequate. Its output is also narrated self-report, which enters at the `assertion` floor and can never rise on its own — a builder describing their own reach is not a measurement of it, and this vault's ladder is right to say so.

**Contrast with neighbors:** [[Full builder thinking-trace visibility with a self-reflection communication gauge]] consumes a trace the agent already has and audits whether *the agent's* instructions landed. This candidate solicits a trace that does not exist yet and asks what *the collaborator* can do. [[Continuous story-based interview habit]] is the same family of act — asking a person — but aimed at customers and needs, not at collaborators and capability.

**Cost shape:** near-zero to build, recurring social cost forever, and its yield decays the moment answering starts to feel like paperwork.

## Definition of done

[[Offer the deposit prompt and count who comes back a second time unasked]]

`npx vitest run test/adapters/deposit-prompt.test.ts`

The spec asserts the containment this node stakes its honesty on: the collaborator's answer is stored verbatim, nothing is inferred from it, and the evidence it produces enters at the `assertion` floor and cannot be promoted by the deposit path itself. That last clause is the important one — the node says outright that narrated self-report "can never rise on its own", and a channel that could quietly promote its own output would break the ladder rather than feed it. Red today because no deposit channel exists in any adapter.

**What a green here does not settle, and it is the chief risk verbatim.** Voluntary compliance is not randomly distributed. The collaborators whose capability is least legible from artifacts are the least likely to sit and write a paragraph, so the profile ends up richest exactly where it was already adequate — and a spec proving the storage is faithful proves nothing about who chose to fill it in. Who comes back a second time unasked needs real collaborators, and the yield decaying "the moment answering starts to feel like paperwork" is a thing only time and people reveal.

## History
- 2026-08-05 unlinked [[Offer the deposit prompt and count who comes back a second time unasked]] — moved under [[Asked at the moment the reasoning is still in their head, a collaborator will deposit it — and come back unasked]] — the belief this test measures now has a node of its own
