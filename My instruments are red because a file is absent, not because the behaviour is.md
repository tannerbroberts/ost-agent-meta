---
type: Opportunity
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[An instrument records whether the pass that wrote it could see the repository]]
[[An instrument naming a spec path that does not exist is refused]]
[[A pass that cannot see the repository cannot set an instrument at all]]

An instrument earns its place by being a falsifiable prediction: it names behaviour that does not exist yet, fails today, and goes green when the solution is built. There are two ways for it to fail today, and they are worth very different amounts.

The strong one is a spec whose assertions go red against code that is really there — it names the module that would have to change, so the builder reads it and knows what to do. The weak one is a spec whose only red is that the path does not exist. That command also fails today and also passes when the solution is built, so it satisfies every check the tool applies, and it hands the builder nothing beyond "create this file."

Which of the two an agent can write depends entirely on whether it can see the repository. Without repo sight, the weak form is the only form available, because naming a real module's real shortfall requires having read that module. The tree therefore fills up with the weak kind and nothing in it records the difference — a grounded instrument and a guessed one are the same string in the same field.

## What was observed

On 2026-08-07 a maintenance pass called `ost_read_repo` to ground its instrument work and was refused: *no product repos configured — add local repo paths under `product.repos` in ost.config.yaml so the agent can read what the product is*. The same pass had already been denied direct filesystem access to the product checkout. Both senses that could have grounded an instrument were shut, and the pass could still have written instruments — the tool would have accepted them. Nothing at the boundary distinguishes an instrument written with sight from one written without it.

## Why this bites hardest here

`ost_next_work` reported 61 solutions whose tests are prose only. That backlog is exactly the work that most needs repo sight, and the surface that is asked to clear it is the surface least able to see. A pass that clears it blind converts prose debt into missing-file debt, which reads as progress in every count the tree keeps.

## History

- 2026-08-07 — Created from a first-party observation during an unattended maintenance pass: `ost_read_repo` refused for want of `product.repos`, immediately before instrument-repair work.

## A weak red observed end to end, and it partly argues against this node — 2026-08-09

This node was created from the writer's side: a pass denied repo sight, therefore able to write only the weak form. The vault now holds one complete lifecycle of a weak-red instrument, both ends machine-recorded, and it is worth reading because it does not go the way this node implies.

**The instance.** "Declare a required tool set and check a pass refuses before doing any work" names `npx vitest run test/mcp/preflight-required-tools.test.ts`. Its `## Instrument Log`:

- **2026-08-06 red (exit 1)** — `No test files found, exiting with code 1`. That is the weak red in its purest form: the command failed because the path did not exist, and for no other reason.
- **2026-08-07 green (exit 0)** — 9.00s, tests ran.

Between the two, session `48c870d7` (2026-08-07T14:23:33Z, a builder session) ran `ls` against that exact path and got `No such file or directory`, then went on to edit `src/knowledge/ruleset.ts` and `docs/reference/v1-readiness.md`. So the sequence is complete and observed: weak red written → builder orients by checking the path → builder builds → green inside 24 hours.

**Why this cuts against the node, and how far.** The node's claim is that the weak form "hands the builder nothing beyond 'create this file.'" In this instance that was enough. The builder was not stranded; it read the test's threshold — *"Required-missing produces zero vault writes and names the absent tool; would-use-missing completes normally"* — which is carried in the node's own `threshold:` field rather than in the spec, and built to that. The threshold did the work the spec path could not.

That is one case, n=1, and the builder here was an agent with full repo access working on a mechanism it had context for. It does not show the weak red is fine in general. What it does show is that **the weak red is not inert**, and that the thing rescuing it is a well-written pre-committed threshold sitting beside it.

**What this suggests about which solution to prefer, stated as a question rather than an answer.** Two of the three candidates below refuse or restrict the weak instrument ("An instrument naming a spec path that does not exist is refused"; "A pass that cannot see the repository cannot set an instrument at all"). This instance is a case both of those would have blocked, and it ended green in a day. The third — "An instrument records whether the pass that wrote it could see the repository" — would have labelled it without blocking it, and is the only one of the three this evidence does not argue against.

**The honest counterweight.** One success does not price the failures, and the failures are the ones that leave no trace: a weak instrument nobody builds simply sits in the tree looking like coverage, and there is no log entry for that. This vault holds 340 tests and, per the rollup, zero recorded runs across every bucket — so the observed-green case is by construction the rare one. The right reading is that the weak red *can* work when a threshold carries it, not that it usually does.

_Sources: the `## Instrument Log` on "Declare a required tool set and check a pass refuses before doing any work" (recorded exit codes, first-party) and `TRANSCRIPT:48c870d7-8192-478a-bdc1-f4aef040cce3` (observed). Grounds feasibility and usability, not demand. No result recorded by this pass and this node's rung is unchanged._

## The weak form counted, and it was almost all of them — 2026-08-09

This node was created from the writer's side and later softened by one observed success. What was missing from both was the size of the thing. Counted across the vault on 2026-08-09:

- 342 assumption tests, 267 carrying an `instrument` field.
- 266 with a recorded observation. **260 of those reds read `No test files found`.**
- 241 named a spec path that does not exist in the product repo.
- 25 named a spec that does exist.

So the weak form was not an edge this node was watching for — it was 98% of the tree's recorded evidence that its own tests were capable of failing. Every one of those 241 also cleared `buildPermit`, whose stated reason is *"`<command>` fails today and passes when `<solution>` is built. That is the definition of done."* An empty file satisfies that sentence.

`knowledge/instruments.ts` justifies the closed instrument form on the grounds that "an agent cannot author the outcome — only name the file". That argument holds exactly while the file exists. Naming one that does not authors the outcome completely, which is why the counts above are not a coincidence: the cheap path produced a guaranteed red.

## What was built, and how this node's own evidence changed it — 2026-08-09

A run that collects no spec is now observed `no-spec` rather than `red` (`src/ost/instrument.ts`). It is **filed, not refused** — the fact that a spec was never written is the actionable half, and refusing would leave the node looking un-run instead.

The first design refused the permit for every weak red. **This node's 2026-08-09 addendum argued against that and changed it.** That addendum records a complete weak-red lifecycle — "Declare a required tool set and check a pass refuses before doing any work", red 2026-08-06 on `No test files found`, green 2026-08-07 — where the builder found the path empty and built to the node's pre-committed threshold instead. A blanket refusal would have blocked the one weak-red lifecycle this vault has watched succeed, so the bar became the threshold rather than the file: a weak red keeps its permit when the test names a **bound** threshold, and loses it only when there is neither a spec nor a fixed bar.

Measured against this vault before shipping: of 241 affected permits, **180 stand and 61 are withdrawn**. The 61 are those handing a builder neither a spec nor a number.

Two ways out are named in the refusal, because either is a real fix and the builder picks: write the failing spec, or pre-commit the bar.

**What this does not settle.** It is a feasibility change, verified by spec (`test/eval/vacuous-red.test.ts`) and by the counts above. It says nothing about whether the 61 withdrawn permits were work anyone wanted, and nothing about desirability, viability or usability. It also does not show that the 180 kept permits are good — only that this vault's one observed case says a bound threshold can carry a builder through a missing spec, on n=1.

_Sources: first-party counts over this vault's own node files and instrument logs, and the recorded observation cited in the addendum above (observed). No result recorded; this node's rung is unchanged._
