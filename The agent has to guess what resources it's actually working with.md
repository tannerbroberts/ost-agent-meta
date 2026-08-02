---
type: Opportunity
status: unvalidated
source: 'human:conversation'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[The same agent has a different tool surface on every surface I run it on]]
[[A declared resource manifest the planner must cite before it ranks anything]]
[[Constraint profile mined from what actually blocked the loop]]

**The need (customer's voice):** "The OST-Agent shouldn't have to guess what its resources are." (Founder, verbatim, 2026-07-25.) The founder's own examples, kept in their words because each names a different resource class:
- "If a project is in the middle of a seed round, and has a million dollars it needs to spend intelligently, THAT'S WORTH KNOWING!!!" — capital, and its deployment deadline.
- "If a user isn't willing to talk to other people, that's a significant limitation." — the operator's social reach.
- "If the human in the loop doesn't want any part of it, know that." — human availability and appetite.
- "If the user WANTS to spend their token budget from an AI platform subscription as soon as the token limit reset time hits, that's an incredibly important functional constraint." — compute economics and its schedule.

**Why it matters:** Every plan the agent makes — which test to run, which solution to ideate, what to rank first and why — is implicitly conditioned on resources it was never told about. These are not subtle signals that must be inferred; they are *declarable facts the operator already knows* and would state if asked, and there is nowhere to put them. The founder flagged the prior framing directly: "I've previously mentioned 'getting to know its builder', but that's an understatement" — see [[The agent has no picture of what the builder can do, because reasoning traces never reach it]], which covers *inferring collaborator capability from traces*; this node covers *declared project resources and operating constraints*, a different mechanism (declaration vs. inference) and a different scope (the project's world, not one collaborator's skill).

**Observed cost of guessing, from this vault's own history (same day):** the cold-offer test was sequenced RUN FIRST on 2026-07-24 and declined by the founder on 2026-07-25 — "that isn't going to fly" — because it presupposed cold outreach the operator was never willing to do. A declared social-reach constraint would have redirected that planning before it was drafted. Likewise [[I need the tree's output to be actionable by compute alone, because my hours don't exist]] and [[Every run ends blocked on a credential only I hold]] are individual constraints of exactly this kind, each discovered the expensive way and each currently living as prose in an opportunity node rather than as a fact the planner consults.

**Direct dependency:** [[Show me the whole priority order, and why each item sits where it does]] — a priority ordering's "why" is only as good as the resource picture it's conditioned on. A project with a million dollars and a deadline ranks differently than one with zero human hours and a token-reset schedule; without declared resources, every rationale silently assumes some default operator.

**Litmus test:** More than one way — a declared resource/constraint manifest the operator fills in and amends (config-level, consulted by prioritization); an onboarding interview that elicits it; constraint fields carried on the Outcome node; budget-aware pass scheduling (the token-reset example is literally a scheduler input); periodic re-confirmation since resources change (a seed round closes, a human's appetite shifts). Distinct mechanisms, real trade-offs. Passes.

**Placement:** Top-level under the Outcome — it conditions planning across every branch rather than belonging to any one of them.

Evidence: founder statement in conversation, 2026-07-25.

## History
- 2026-07-25 evidence: (none) → assertion — founder-stated need, verbatim examples preserved; no external party involved; floor rung per the ladder's rule.
