---
type: Opportunity
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: observed
authorship: machine
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

## A sharper class inside the weak red — the directory is not there either — 2026-08-10

**This is not a fourth census and should not be read as one.** The 2026-08-09 section already counted the weak form at 241 absent paths against 25 present, and re-measuring today gives 27 present against 250 absent out of 277 instrument fields. Same tree, same method, one day apart — that is persistence, not corroboration, and nobody should count it as a second measurement.

What this pass adds is a partition of the absent 250 that the earlier count did not draw, made possible by listing the product suite directory by directory rather than testing paths one at a time.

**Seventeen instruments name a top-level `test/` subdirectory that does not exist.** The suite has twenty: `adapters`, `automation`, `cli`, `config`, `eval`, `fixtures`, `friction`, `git`, `knowledge`, `loop`, `mcp`, `ost`, `processes`, `product`, `release`, `runner`, `security`, `skill`, `telemetry`, `web`. These seven are named by instruments and are not among them:

| Phantom directory | Instruments naming it |
|---|---|
| `test/instruments/` | 4 |
| `test/preflight/` | 3 |
| `test/tools/` | 3 |
| `test/guards/` | 2 |
| `test/evidence/` | 2 |
| `test/gate/` | 1 |
| `test/rank/` | 1 |

**Why this is worth separating from "the file is absent".** A missing file inside a real directory is a builder writing one spec beside its neighbours, and the surrounding files tell them the conventions, the fixtures, and what the module under test is called. A missing file inside a missing directory tells them none of that: the author was inventing repository structure, not just a filename, and the builder's first decision is whether this product should have a `test/gate/` at all. That is a design question arriving disguised as a spec path, and it is the weakest form of red this tree can produce — weaker than the weak red this node was created to name, because the earlier form at least pointed at a real neighbourhood.

**The instance that makes the point.** "Every solution in the current backlog has an existing spec that could go red for it" — the assumption whose whole subject is whether a real spec can be found for each backlog solution — carries `npx vitest run test/instruments/spec-path-resolution.test.ts`, in a directory that does not exist. Its own node already says so in prose (*"Written without repo sight, so the path is invented"*), and its Instrument Log records the 2026-08-07 red as `No test files found`. That is the tree predicting its own result correctly and having no way to act on it.

**What this does not settle.** Whether the seven phantom directories are bad ideas — a product may well want a `test/instruments/`, and three of the four instruments naming it are about the instrument machinery, which currently has its specs spread across `test/ost/instrument.test.ts` and `test/knowledge/instruments.ts`. The finding is only that seventeen instruments encode an unmade structural decision, and that no amount of building the named behaviour makes them resolve until somebody makes it. It says nothing about desirability, viability, or usability, and no test was run.

_Method: `ost_read_repo` listings of every directory under `test/` in the OST-Agent repository, matched against every `instrument:` field in this vault, 2026-08-10. Read of committed code and of this vault's own nodes; no command was executed and no result recorded. This node's rung is unchanged._

## The phantom-directory table re-checked eleven days on — five of seven are now real — 2026-08-21

The 2026-08-10 section above listed seven `test/` subdirectories named by instruments and absent from the product suite, and argued that a missing file inside a *missing* directory is the weakest red this tree can produce because the author was inventing repository structure rather than a filename. That table is a falsifiable claim about the repository, so this pass re-ran it against today's checkout. It has largely resolved.

| Phantom directory (2026-08-10) | Instruments naming it | State on 2026-08-21 |
|---|---|---|
| `test/instruments/` | 4 | **exists** — `overwrite-guard`, `sight-provenance`, `spec-path-resolution` |
| `test/preflight/` | 3 | **exists** — `manifest-covers-observed-refusals` |
| `test/tools/` | 3 | **exists** — `read-node-body-scope` |
| `test/guards/` | 2 | **exists** — `provenance-census-scores-against-known-defects` |
| `test/evidence/` | 2 | **exists** — `age-out-preserves-novel`, `corroborate-disposition` |
| `test/gate/` | 1 | still absent |
| `test/rank/` | 1 | still absent |

The suite has gone from twenty top-level directories to twenty-seven: the five above plus `compression` and `perf`.

**The instance this node picked out has resolved too.** Line 98 above names "Every solution in the current backlog has an existing spec that could go red for it" as the sharpest case — an instrument about spec-path resolution, pointing at `test/instruments/spec-path-resolution.test.ts`, in a directory that did not exist, with its own prose admitting the path was invented. That file exists today. The structural decision the instrument encoded was made, in the direction the instrument assumed.

**What this changes, and what it does not.** It weakens the strongest version of this node's argument. Fourteen of the seventeen instruments that encoded an unmade structural decision no longer do; the decision got made, and the phantom paths were a reasonable prediction of where the product was going rather than invention. That is the same shape as the n=1 lifecycle recorded in the 2026-08-09 addendum, now at a larger n and about directory structure rather than a single file — so the two observations agree, and both cut the same way.

It does not show the specs *assert this tree's questions*. A directory existing with one file in it does not mean the instrument naming a second file in it will go red for a test-specific reason; it means the neighbourhood is real, which was precisely the distinction line 96 drew as the thing worth having. The `no-spec` count is not re-measured here and this section is not a census — one table, re-checked, eleven days later.

_Method: `ost_read_repo` listings of `test/` and of each of the seven named subdirectories in the OST-Agent repository, 2026-08-21, matched against the table this node already carried. Read of committed code only; no command was executed, no result recorded, and this node's rung is unchanged._

## Why the weak form is the only form this surface can write — measured at the tool boundary, 2026-08-21

The node has argued since 2026-08-07 that "which of the two an agent can write depends entirely on whether it can see the repository." This pass held repo sight and still could not write the strong form, which locates the constraint somewhere the node had not looked: `ost_set_instrument` itself.

Attempting to give an existing test an assertion-specific red inside an existing spec produced two refusals, in this order:

- `npx vitest run test/git/commit-provenance.test.ts -t "every commit carries the session id of the run that made it"` → *"contains shell punctuation. Instruments are run as argv with no shell... Name one spec file."*
- `npx vitest run test/git/commit-provenance.test.ts -t session-id` → *"is not an instrument form. The allowed forms are: vitest-spec (`npx vitest run <path>.test.ts`)."*

So the accepted grammar is a bare spec path and nothing else. A test-name filter — the mechanism by which a command names one assertion inside a file that already exists — cannot be expressed at all.

**Why that forces the weak form.** The strong red requires a command that fails today *inside* a spec that exists. With only a bare path accepted, a named file either passes today (so it cannot fail, and is refused for that) or does not exist (so it fails, as `no-spec`). On a green suite there is no third case. The strong instrument this node was created to ask for is therefore not merely hard to write without repo sight — on this tool surface it is **unwriteable with it**, and every instrument written here is weak by construction.

This is worth separating from the sight argument because it changes what would fix it. Granting repo sight to more passes cannot close this; the grammar in `knowledge/instruments.ts` would have to admit a test-name filter, or the tree would have to accept that a builder's definition of done lives in the `threshold:` field rather than in the command — which is the reading the 2026-08-09 addendum already found evidence for, on n=1.

**What this does not settle.** Whether admitting `-t` is a good idea. The stated reason for the closed form is that "an agent cannot author the outcome — only name the file", and a test-name filter is a string the agent chooses, so widening the grammar re-opens exactly the hole the closed form was built to shut. That trade is a design decision and is not made here. No test was run and this node's rung is unchanged.

_Method: two `ost_set_instrument` calls made during this pass, and their verbatim refusals. First-party observation of the product's own tool boundary; grounds feasibility, not demand._

## 2026-09-01 — the loop's own prompt now instructs every firing to write the form the validator refuses

Kept short, per this branch's convention. Only what is new, and it is about a different artifact than any section above.

**What the 2026-08-21 section established.** The accepted grammar is a bare spec path and nothing else; a test-name filter "cannot be expressed at all", so the strong instrument is unwriteable on this surface even with repo sight. That finding is re-verified current this pass by first-party read rather than by refusal: `INSTRUMENT_FORMS` in `src/knowledge/instruments.ts` holds exactly one entry, whose pattern is `^npx vitest run (?<target>[A-Za-z0-9][A-Za-z0-9._/-]*\.test\.ts)$`, and `SHELL_METACHARACTERS` includes both quote characters. Unchanged in the eleven days since.

**What is new.** The unattended sweep's own firing prompt now holds up that refused string as its worked example of quality, and instructs each pass to prefer it. Its words: "`vitest run test/git/conflict-guard.test.ts -t \"refuses a write whose base hash drifted from the last read\"` against a spec that exists and asserts real behavior is strong — it fails today for a reason specific to this test", set against the bare path, which it calls weak and says "hands a builder nothing but 'create this file.'" Step 4 then directs the firing to write the former.

That instruction is unsatisfiable. The example fails the parse three ways over: the double quotes trip `SHELL_METACHARACTERS`, the `-t` filter matches no form, and both examples omit the leading `npx` the pattern anchors on. So the loop instructs each firing to produce a string its own validator rejects on sight, while calling the only accepted string the weak kind not worth writing.

**Why this is worth recording separately from the grammar finding.** The 2026-08-21 section frames the constraint as a limit a pass discovers at the tool boundary. It is now also a standing instruction to walk into it. The cost is not just the refused call: a refusal is a `tool_error`, the harvester files it, and the record joins `unmappedEvidence` — where it cannot be retired, per the census on "A human-edited manifest of loop-prescribed call sequences the harvester suppresses". So the contradiction manufactures queue debt on the same surface that is being asked to clear it. This pass avoided that only by reading the validator first and declining to make the call, which is not something the instruction suggests.

**The repair is a choice between two artifacts, and it is not made here.** Either the grammar admits a test-name filter — which the 2026-08-21 section already notes re-opens the hole the closed form exists to shut, since a filter string is one the agent chooses — or the firing prompt stops asking for a form the product refuses and says plainly that a bare spec path is the only expressible instrument, with the `threshold:` field carrying the builder's definition of done. The second is free and matches what the 2026-08-09 addendum found evidence for on n=1. Whoever owns the prompt should pick.

**What this does not settle.** Nothing about whether `-t` should be admitted, nothing about the 250-odd absent paths this node counts elsewhere, and nothing about desirability, viability or usability. It is a statement about two artifacts disagreeing, not about whether either is right.

**Limits.** The prompt text quoted above is this firing's own instructions, read as given; a reader wanting to confirm it should check the loop's prompt template rather than take this node's word. No `ost_set_instrument` call was attempted this pass, so the refusal is inferred from a first-party read of the validator rather than observed at the boundary — that is weaker than the 2026-08-21 evidence and is offered as corroboration of it, not as a second measurement.

_Method: `ost_read_repo` reads of `src/knowledge/instruments.ts` and `src/ost/instrument.ts` in full, against this firing's own prompt. Nothing executed, no rung moved, no instrument set, no status changed, no node created._

## 2026-09-02 — the refusal this node could only infer is now machine-recorded, three times across two days and two different tools

Kept short, per this branch's convention. This adds exactly one thing: the observation the section above named as its own weakness.

**What that section flagged as missing.** Its limits paragraph reads: "No `ost_set_instrument` call was attempted this pass, so the refusal is inferred from a first-party read of the validator rather than observed at the boundary — that is weaker than the 2026-08-21 evidence and is offered as corroboration of it, not as a second measurement." The claim was that the loop's own prompt instructs every firing to write a string the validator rejects. It was argued from two artifacts, not from anything anyone had watched happen.

**It has been watched happen, by a recorder with no narrator.** `USAGE:2026-09-01` is a mechanical rollup of the append-only tool-invocation trace. That day ran **491 calls, 489 ok, 2 failed — and both failures are this refusal**, in two different tools:

- `ost_create_node`, on "A test born humans-required at creation is in the queue with a non-null age", refused with *"contains shell punctuation. Instruments are run as argv with no shell"* against an instrument carrying a `-t` filter in double quotes.
- `ost_set_instrument`, on "An all-cautious solution leaves the instrument bucket while one with a runnable test beside it stays", refused against an instrument of the identical shape.

**And again today, so it is not a one-day artifact.** `TRANSCRIPT:3408957c-0db6-40d9-a9d8-35680c42f517`, session-stamped 2026-09-02T07:29:53Z, records `ost_create_node` refused on "The harvester carries the caller's declared expectation through to the friction event" for an instrument naming `test/adapters/transcript.test.ts` with a `-t` filter. Three refusals, three sessions, two days, two entry points.

**The consequence this node predicted is also now observed, end to end.** That section reasoned: "a refusal is a `tool_error`, the harvester files it, and the record joins `unmappedEvidence` — so the contradiction manufactures queue debt on the same surface that is being asked to clear it." The 2026-09-02 refusal above was harvested into a friction record, and that record was one of the two new items **this firing's own `ost_ingest_inbox` captured**. The loop instructed a pass to write a refused form, the refusal became evidence, and the evidence arrived in the queue of the next pass. That is the full cycle, first-party, inside twenty-four hours.

**What this changes about the strength of the finding, stated no wider than it goes.** The 2026-09-01 section offered itself as corroboration rather than a second measurement. It can stop doing that: the boundary refusal is now recorded by the usage trace and the friction harvester independently of any agent's account of it, which is the one evidence class in this tree that no pass composed. It does not settle the repair — the choice between admitting a test-name filter and fixing the prompt is unchanged and is still a human's. It also says nothing about whether the two refused instruments were good tests; only that the form their authors reached for is the form the prompt recommends and the product rejects.

**Limits.** The usage rollup prints only the first three failed calls and truncates each; the first 2026-09-01 entry names shell punctuation explicitly, while the second is cut off before its reason and is classed here by the identical `-t` construction in the visible portion rather than by a quoted refusal. Three sessions is not a rate over the 21 sessions that day. Nothing was executed, no instrument set, no rung moved, no status changed, and no node created — the two refused tests named above are other passes' work and were not touched.

_Method: first-party reads of `.ost-agent/evidence/USAGE_2026-09-01.md` and `.ost-agent/evidence/TRANSCRIPT_3408957c-0db6-40d9-a9d8-35680c42f517.md` from disk, plus this firing's own `ost_ingest_inbox` result. Machine-recorded observation of the tool boundary; it grounds feasibility and usability, not demand. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design._
