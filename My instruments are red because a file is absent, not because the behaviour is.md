---
type: Opportunity
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

An instrument earns its place by being a falsifiable prediction: it names behaviour that does not exist yet, fails today, and goes green when the solution is built. There are two ways for it to fail today, and they are worth very different amounts.

The strong one is a spec whose assertions go red against code that is really there — it names the module that would have to change, so the builder reads it and knows what to do. The weak one is a spec whose only red is that the path does not exist. That command also fails today and also passes when the solution is built, so it satisfies every check the tool applies, and it hands the builder nothing beyond "create this file."

Which of the two an agent can write depends entirely on whether it can see the repository. Without repo sight, the weak form is the only form available, because naming a real module's real shortfall requires having read that module. The tree therefore fills up with the weak kind and nothing in it records the difference — a grounded instrument and a guessed one are the same string in the same field.

## What was observed

On 2026-08-07 a maintenance pass called `ost_read_repo` to ground its instrument work and was refused: *no product repos configured — add local repo paths under `product.repos` in ost.config.yaml so the agent can read what the product is*. The same pass had already been denied direct filesystem access to the product checkout. Both senses that could have grounded an instrument were shut, and the pass could still have written instruments — the tool would have accepted them. Nothing at the boundary distinguishes an instrument written with sight from one written without it.

## Why this bites hardest here

`ost_next_work` reported 61 solutions whose tests are prose only. That backlog is exactly the work that most needs repo sight, and the surface that is asked to clear it is the surface least able to see. A pass that clears it blind converts prose debt into missing-file debt, which reads as progress in every count the tree keeps.

## History

- 2026-08-07 — Created from a first-party observation during an unattended maintenance pass: `ost_read_repo` refused for want of `product.repos`, immediately before instrument-repair work.
