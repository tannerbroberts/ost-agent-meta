---
type: Opportunity
source: 'TRANSCRIPT:7e982096-36c5-4ac2-a23f-75865bc4bf8e'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Derive the whole consequence set from the premise and ask about all of it at once]]
[[Bank each question, proceed on a stated default, and present the banked set at the end]]

I asked for one change and was stopped seven separate times to answer for it. Every stop was reasonable on its own. Taken together they were one decision, asked in seven pieces, because answering the first piece did not tell the run anything about the six that followed from it.

## What the evidence shows

`TRANSCRIPT:7e982096-36c5-4ac2-a23f-75865bc4bf8e` — 7 friction events in one session, all of them `clarifying_question`, no tool errors at all. Every question descends from a single premise the operator had already stated ("only serve Claude subscription users"):

1. Does that mean changing how it ships, or also cutting the API-key-billed autonomous runner?
2. How should the plugin start the MCP server once npm is gone?
3. What happens to the already-published `ost-agent` package on npm?
4. Where should the implementation happen — isolated worktree or in place?
5. The refusal message now exists as two identical string templates, violating the plan's own single-sourcing constraint — how to resolve?
6. `ost-agent tool ost_status` throws as of this commit, and the next task deletes that command entirely — reviewer says needs fixes, plan says delete. Which?
7. Deleting the runner severed evidence ingestion and the MCP surface never had it — how should we close it?

Questions 1 through 4 are all consequences of the shipping decision. Questions 5 through 7 are consequences of the implementation route chosen in 4. The session did no work between several of them.

## What I actually want

To state the premise once, and have the run derive from it — asking me only where the premise genuinely underdetermines the answer, and telling me at the outset roughly how many such places it expects to find.

## What this does not claim

Some of these were good questions. Question 7 in particular surfaced a real severed capability that a silent run would have shipped broken. The complaint is not that I was asked; it is that I was asked serially, with no view of how many more were coming, in a session where the alternative was to bank them and continue.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from a session transcript. It grounds usability, not desirability, and is not outside-user evidence of want.
