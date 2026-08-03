---
type: Opportunity
source: 'TRANSCRIPT:06eba571-9780-458a-b384-da5abe101e6f'
created: '2026-08-03'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Non-interactive is the default, and any tool that would prompt is made to fail loudly instead]]
[[Settle the standing answers once, in committed configuration the run inherits]]
[[Detect that no terminal is attached and answer the prompt from a stated policy]]

When I hand work to a run that is meant to finish on its own, it does not fail — it stops, mid-command, at a question a tool asked expecting a human at a keyboard. Nothing about the stop announces itself as a stop. The run is simply still there, holding, until I happen to look.

The distinguishing thing is that this is not a decision I would want to be asked about. A tool defaulted to interactive because it could not tell nobody was watching. I would have answered every one of these the same way, every time, without thinking — which is exactly why being asked costs the whole run.

## What the evidence shows

- `TRANSCRIPT:06eba571-9780-458a-b384-da5abe101e6f` — `git` exits 128 with `hint: You have divergent branches and need to specify how to reconcile them. hint: You can do so by running one of the following …`. The reconcile policy is a one-time config; the run had no way to have set it.
- `TRANSCRIPT:e42cd03d-b2a4-44ba-989a-9e01cc368f77` — `overwrite src/web/budget.ts? (y/n [n]) not overwritten`. The prompt timed out to its default and the file was silently left alone; the command reported exit 1 rather than "I asked a question nobody heard."
- `TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f` — a second `git` exit 128, `fatal:` truncated, in a directory listing that shows the repo was not where the command assumed.

## Why this is not the sibling need

The parent opportunity is about a loop that is genuinely blocked on a human decision and has no way to say so. This one is narrower and different in kind: there is no decision here at all. The correct answer was determined in advance in every case, and the stop is purely an artefact of a tool that could not detect it was running unattended.

Evidence class: observed behaviour of the agent's own usage, captured mechanically from session transcripts. It grounds usability, not desirability, and is not outside-user evidence of want.
