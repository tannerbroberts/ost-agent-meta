---
type: Opportunity
source: 'USAGE:2026-08-04'
created: '2026-08-05'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A runner that executes instruments and records exit codes only, judging nothing]]
[[Ration instrumenting against the rate results are recorded, so readiness cannot outrun execution]]
[[Stop counting an unrun test as progress, and report execution as the only number that moves]]

A whole day's work goes into making tests runnable and the number of tests that have run stays at zero.

The machine-recorded trace for 2026-08-04 is 356 tool invocations, of which 88 are `ost_set_instrument` — a quarter of the day spent attaching commands to tests that already had thresholds. Against that, every bucket in the tree's own rollup reports `tested 0`. Not "tested few": zero, across 255 assumption tests, for the life of the tree.

So the pipeline has a specific shape of blockage, and it is not the one the tree keeps working on. Writing a test is cheap and happens constantly. Giving it a threshold is done. Giving it a runnable command is being done at scale. **Executing it is on nobody's surface at all** — the unattended pass is forbidden from running tests, and recording a result is a human's `ost-agent result`. Every automated hand that touches a test can only ever make it more ready to run, so readiness is the only thing that accumulates, and it accumulates forever.

The felt version, from the operator whose hours don't exist: I am paying compute to prepare work for a person who was the bottleneck in the first place. Instrumenting all 255 would leave me with 255 commands and still nothing I can point at and say it passed.

There is more than one way to address it — which is what keeps this an opportunity. Something could run instruments and record only their exit codes, without judging what a green means. The verdict step could be split so the mechanical half needs no person. Instrumenting could be rationed against the rate results actually get recorded, so readiness cannot outrun execution. Or the tree could stop counting an instrumented-but-unrun test as progress at all, and say plainly that the number that matters has not moved.

Evidence class: machine-recorded trace of tool invocations, no narrator. Declared at `assertion` because a usage trace records what this agent did with its own tools — it is not a measurement of the need, and a prior call on this same channel was correctly refused when it tried to claim otherwise. It grounds the agent-tool loop, never external demand.

## The specific gate, measured — 2026-08-05 unattended sweep

The prose above says execution "is on nobody's surface at all." That is right, but it is one level too general to act on, and this sweep found the exact field that stops it.

**Counted over the vault, not estimated:** 200 of the tree's 272 assumption tests now carry an `instrument:` of the form `npx vitest run test/…`. That is 73% of every test in the tree holding a command that a machine could execute unattended.

**Against that, `ost_next_work` reports `runnable: 0`.** Not few — zero. It also reports `awaitingOneCommand: 0` and `blockedOnPermission: 0`, and puts all 272 tests in `needsHumans`. So every one of the 200 commands is classified as requiring a person.

**The mechanism is one unset frontmatter field.** A grep for `^lane:` across all 920 nodes returns exactly one hit, on "Ask five operators whether they would let a stated default stand while they are away", and that one is *empty*. No node in this tree has ever been assigned a lane. `needsHumans` is therefore not a judgement anything made about these 200 tests — it is the default that applies when the field is absent, and the sweep is reading silence as "a person must do this."

**Why that is the whole blockage.** Setting a test compute-only is `ost-agent lane --set` on the CLI, deliberately a human's call — the agent surface holds only `ost_flag_humans_required`, which can just *remove* work from compute's reach, never grant it. So no automated hand can move a test from `needsHumans` to `runnable`, no matter how good its instrument is. Readiness accumulates because the one transition that converts readiness into permission is the one no pass can make.

**What this sharpens about the three solutions beneath.** "A runner that executes instruments and records exit codes only" is the sibling that looks like the answer, but a runner would still have nothing to run: it would ask which tests are compute-only and be told none are. The cheapest unblock in the tree right now is not a build at all — it is a human spending one session assigning lanes to the 200 tests that already have commands. That is worth stating plainly because it is a case where the tree's recommended work and its actual constraint have come apart, and this sweep has now spent a fourth pass adding readiness to a pipeline whose gate is downstream of everything it can touch.

**Left for a human, not decided here.** Whether all 200 deserve the compute-only lane is exactly the judgement the lane exists to protect — a good number of them name people in their methods and should stay `needsHumans`. The claim is only that *nobody has ever made that call for any of them*, so the current zero reflects an unmade decision rather than 272 considered ones.

_Established by direct measurement of this vault on the 2026-08-05 unattended sweep: `^instrument: npx` matches 200 files, `^lane:` matches 1, and `ost_next_work` reports 0 runnable. Observed behaviour of the tool surface and the tree's own state; grounds usability, not demand._

## Confirmed first-party, one day later — 2026-08-06

The 2026-08-05 measurement found 200 instrumented tests, 1 `lane:` field, 0 runnable. Re-measured on this vault today:

- **232** nodes carry `instrument: npx …` — up 32 in one day.
- **4** nodes carry a `lane:` field. All four read `humans-required`. Not one node in this tree has ever been assigned `compute-only`.
- `ost_next_work` still reports `runnable: 0`, `awaitingOneCommand: 0`, `blockedOnPermission: 0`, and **301** tests in `needsHumans` — up from 272.

So readiness grew by 32 and execution stayed at zero, which is the pattern this node named, holding exactly.

**This pass confirmed the gate by walking into it, which is better evidence than counting.** It created 9 assumption tests, 8 of them carrying a `vitest` instrument, and wrote `**Lane: compute-only.**` as the opening line of every one of those 8 bodies — because each is genuinely settled by a spec file over the vault or the repository, with no person anywhere in the method. All 8 landed in `needsHumans`. "Auto-satisfy a read-before-write, then change the file underneath and require the write to still refuse" is visible there in the sweep output, alongside tests that name interviews and willingness-to-pay probes.

That is the ruleset behaving exactly as written — prose is never promoted to a label, and only `ost-agent lane --set` moves what compute may run — and it is worth recording because it closes the last gap in this node's argument. The 2026-08-05 finding could still have been read as neglect: 200 tests nobody had got round to labelling. It is now demonstrated that a pass *actively declaring* a test compute-only, in the sanctioned place, with a runnable command attached, cannot move it. The default is not unset because nobody looked. It is unmovable by anything that runs unattended.

**The compounding cost, stated plainly.** Every unattended pass that does its job well makes this worse. This one added 8 more commands to a queue of 232 that nothing may execute, and it did so while following the instructions it was given. A fifth pass has now added readiness to a pipeline whose gate is downstream of everything it can touch.

**Unchanged and still the cheapest unblock in the tree:** one human session assigning lanes. Whether all 232 deserve `compute-only` is precisely the judgement the lane exists to protect, and a good number name people in their methods and should stay where they are. The claim remains only that the call has never been made for any of them.

_Direct measurement of this vault, 2026-08-06: `^instrument: npx` matches 232 files, `^lane:` matches 4 (all humans-required), `ost_next_work` reports 0 runnable and 301 needsHumans. Plus first-party observation of 8 instrumented compute-only-declared tests created this pass, all classified needsHumans on the next sweep._

## Measured — an instrument does not make a test runnable, and only a human's label can (unattended sweep, 2026-08-06)

This node asks why nothing ever runs. This pass hit the mechanism directly, by creating three tests and watching where they landed.

**What was done.** Three `#AssumptionTest` nodes were created with `instrument:` set and no `humansRequired:` — deliberately compute-answerable questions (replay recorded sessions, compare two hashes, replay working-tree states), each declaring `**Lane: compute-only.**` in its own prose. `ost_next_work` before the writes reported `runnable: 0` and `needsHumans: 307`. After: `runnable: 0` and `needsHumans: 310`. All three went to the humans-required lane.

**Why.** The created files carry `threshold:` and `instrument:` in frontmatter and **no `lane:` field at all**. An unset lane counts as needing a person, and the prose declaration does not promote it — the ruleset says so outright: nothing ever promotes prose to a label, only a human's `ost-agent lane --set` moves what compute may run. The one lane tool an agent holds, `ost_flag_humans_required`, moves work in the restrictive direction only, and is not on this surface in any case.

**This is not an artefact of new nodes.** Three tests already in the tree carry instruments and sit in `needsHumans` on the same sweep:

| Test | Instrument |
| --- | --- |
| "Blind-review a pass's acknowledge-or-map calls on the seven stranded items" | `test/ost/evidence-acknowledge.test.ts` |
| "Audit every shipped solution against the repository before trusting the exclusion" | `test/ost/shipped-status-audit.test.ts` |
| "Acceptance rate of five self-drafted ruleset changes" | `test/knowledge/ruleset-proposal.test.ts` |

**So the loop this node names is closed, and closed by design.** Passes are instructed to write instruments; instruments are what a compute-only lane would need; but the label that admits a test to the compute lane is reachable only from the CLI. `runnable` is therefore structurally 0 for everything any pass has ever authored, which is exactly what the rollup shows: every bucket in this tree reads `tested 0`, across 310 tests.

**What this does not claim.** That the gate is wrong. A human holding the permissive label is the same principle that stops an agent clearing its own evidence gate, and it is defensible. What it does mean is that "write more instruments" cannot on its own change the tested count, and no unattended pass can move that number by any amount of correct work.

**The cheapest thing that would test the fix:** take the three instrumented tests named above, run `ost-agent lane --set` on them, and see whether `runnable` becomes 3 and whether an attended session then actually runs them. If it does, the bottleneck is one CLI call per test and the tree can be unblocked in a batch. If it does not, the blockage is somewhere further down and this node's question is still open.

_Source: `ost_next_work` output immediately before and after three `ost_create_node` calls on 2026-08-06, plus direct reads of the created files' frontmatter and of the three existing test nodes named above. Observed behaviour of this product's own sweep. Corroboration only; the node's rung is unchanged._
