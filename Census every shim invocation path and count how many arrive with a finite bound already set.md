---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: zero invocation paths reach the shim without a finite bound
instrument: npx vitest run test/loop/wait-caller-bound-census.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** A census over the corpus and the automation scripts, both already on disk.

**What is being counted.** Every path by which `await` can be reached, and whether each arrives under a clock the shim does not own. Two sources, and both are needed because they fail differently:

- **The corpus.** `test/loop/wait-primitive-affordance.test.ts` already walks `test/fixtures/corrections/*.jsonl` via `corpusCommands()`. Extend it to pull the `timeout` field alongside the `command`, and count invocations that carry no explicit timeout. All six observed give-ups in `TRANSCRIPT:029e4edb-7a41-4ef1-9851-dbe3a4f986b1` carried `"timeout": 400000`, which is the belief's supporting sample and also its whole sample.
- **The scripts.** `examples/automation/build-pass.sh` installs the shim on `PATH`, and anything on `PATH` can be invoked from a script rather than from a tool call. A shell invocation is under no harness clock at all, so a single unbounded call site in the automation is a refutation on its own.

**Why the threshold is zero rather than a majority.** The parent candidate deletes the shim's only bound. One unbounded path is enough to produce the wedged unattended firing that `DEFAULT_FOR_SECONDS`'s own docstring says the bound exists to prevent, and a wedged firing with nobody watching is not averaged away by the paths that were fine. A majority bar would let this pass while leaving the failure it is checking for intact.

**Why it is red today.** `WaitingCase` in `src/loop/wait.ts` carries `id`, `intent`, `session` and `blocked` — the caller's timeout is not among them, and `corpusCommands()` returns only `{session, command}`. The data the census needs is discarded before it reaches any assertion. The builder's first job is to stop discarding it.

**Honest label on the red: `no-spec`, the weak kind.** The named file does not exist, so today's failure is not specific to this question — the argv-only instrument rule leaves no stronger form available to a pass that may not write code. The two named sources, the named fields to stop discarding, and the zero threshold are what the builder gets in place of a blank file.

**What a green run does NOT settle.** Only that the paths seen today are bounded. It cannot cover a path nobody has written yet, which is the standing weakness of proving an absence by census — and it says nothing about whether a harness kill is an acceptable ending, since a kill produces neither the trimmed output nor the give-up line the shim prints today.
