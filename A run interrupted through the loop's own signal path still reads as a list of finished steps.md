---
type: AssumptionTest
created: '2026-08-23'
evidence: assertion
threshold: >-
  0 of 10 runs interrupted through the real `loop start` process overstate what
  landed
instrument: npx vitest run test/loop/journal-cli-interruption.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The belief under test.** The parent assumption claims the harness must expose an interruption hook for a checkpoint line to land. The repository suggests it may not need one: `src/loop/journal.ts` writes forward per completed step, so a kill at any point is already covered without a special callback. But the existing spec proves that only for a *fixture child* — `test/loop/run-journal-interruption.test.ts` spawns `fixtures/journal-interruptible-run.ts` and SIGKILLs it, never the real `loop start` process. The guarantee is therefore established for the journal module and merely assumed for the harness that wraps it, which is exactly the gap the parent solution's own body names as still open: "whether the journal is actually wired into the harness's interruption path rather than only its normal step loop."

**What the spec must assert, concretely.** Spawn `src/cli/index.ts loop start` against a temp vault (the CLI-driven pattern already used in `test/loop/checkpoint-update.test.ts`'s final `describe`, which shells out to `node_modules/.bin/tsx` with `--vault`). Signal the real process mid-run at a seeded step boundary, then read the journal back with `readJournal()` and compare against what actually landed on disk — reusing the overstate/understate comparison `run-journal-interruption.test.ts` already implements in its `landedSteps()` helper, applied to the CLI instead of the fixture. The bar is the one the sibling assertion fixed and this one inherits: no journal may claim a step that did not land.

**Honest statement of what this red is worth — read before trusting it.** `test/loop/journal-cli-interruption.test.ts` does not exist, so this command fails today because the file is absent. That is the weakest reason a command can fail: it would fail identically for any question written on that path, so the red distinguishes nothing and mints no build permit. It is recorded as the strongest form available on this surface, not as a good one.

**Why the stronger form could not be written, verified first-party this pass.** The ruleset asks for a spec that exists plus a `-t` filter naming an absent assertion, so the red is specific. `ost_create_node` **refused that command**: this pass attempted `npx vitest run test/loop/run-journal-interruption.test.ts -t "a run interrupted through the loop's own signal path still reads as a list of finished steps"` and was told it "contains shell punctuation. Instruments are run as argv with no shell, so a command written to be interpreted would not mean what it looks like. Name one spec file." The quoting a `-t` filter requires is exactly what the guard rejects, so on the tool surface the recommended strong form is unreachable and every agent-written instrument is a `no-spec` red by construction. Recorded in full on "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed", which had attributed that outcome solely to repo sight being read-only; this is a second and independent cause.

**What a green here would NOT settle.** Only that the mechanism survives interruption. It says nothing about whether an operator wants a checkpoint log, whether the next pass would trust it over reconstructing state itself, or whether backgrounding (as distinct from a signal) behaves the same — a harness-lifecycle question that stays with the humans-required sibling test beneath this assumption. Feasibility answered here leaves desirability and usability exactly where they were.

**Lane, for whoever sets it.** This node makes no claim about its own lane. `ost_next_work` classified it into `needsHumans` on the pass that created it. Whether it belongs in compute's reach is `ost-agent lane --set`, and a human's call.

_Proposed, not run. No result is recorded and this node's rung is unchanged._

## History
- 2026-08-23 body edited — The node as created opened with "**Lane: compute-only.**" — a lane declared in prose by the agent that wrote it. `ost_next_work` classified the test into `needsHumans` on the same pass, so the node was answering the run-me-unattended question twice and in two different ways. Prose never promotes a test into compute's reach; only a human's `ost-agent lane --set` does. Removing the declaration rather than restating it, so the node carries no claim about its own lane and the label stays the human's to set. Nothing else changed: the belief under test, the assertion the spec must make, the honest accounting of what the red is worth, and the not-settled-by-this list are all carried through verbatim.
