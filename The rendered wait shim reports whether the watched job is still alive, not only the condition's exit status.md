---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
threshold: >-
  at least 3 distinct outcomes — done, still running, gone — are recoverable
  from the wait's exit status and stderr
instrument: npx vitest run test/loop/wait-liveness-verdict.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec must assert, stated precisely so the builder inherits a definition of done rather than a filename.** `renderWaitShim()` in `src/loop/wait.ts` is a pure function returning the shim's text, so this needs no process orchestration to test. Today its give-up branch emits exactly one line:

```
await: gave up after ${waited}s; the condition still exits $rc.
```

That sentence carries the condition's status and nothing about the job. The spec asserts the rendered shim distinguishes **three** outcomes rather than two: the condition succeeded; the condition has not succeeded and the watched work is still alive; the condition has not succeeded and the work is gone. Concretely — assert the give-up branch of `renderWaitShim()` emits a distinguishable marker for the still-alive case, and that the two non-success outcomes do not collapse to one exit status.

**Why it fails against today's code, specifically rather than vacuously.** `renderWaitShim()` has no liveness check in it at all: the loop's only inputs are the condition's exit code and the elapsed count, and the give-up message is a fixed string. An assertion that the still-alive case is distinguishable fails on the rendered text, for a reason belonging to this question and no other. Change the question and the assertion changes with it.

**Honest disclosure about the red this currently produces.** `test/loop/wait-liveness-verdict.test.ts` does not exist yet, so today the command exits non-zero as `no-spec` — the weak red the ruleset warns about, which would fail identically for any question written on that path. It is filed that way deliberately rather than hidden: this surface cannot author spec files, so the strong red is not reachable from here. What is reachable is naming the module, the function, its current output and the assertion, which is what the paragraphs above do. The test is not finished until that spec exists and the assertion fails; whoever writes it should get a red on the assertion before writing any implementation.

**What a green here does NOT settle, and this is the important half.** A passing spec proves the *rendered shim text* can express three outcomes. It does not prove liveness is decidable for the jobs this loop actually waits on — a detached vitest suite whose parent shell has exited, work in another checkout, a process on another machine. That is the assumption's real risk and the harder half, and it needs the check run against real backgrounded work rather than against a string. Nor does it touch desirability, viability or usability: nobody has said a three-valued wait is what they want, only that a two-valued one expired nine times.

**Not to be confused with the ceiling, which already ships.** The caller-settable give-up bound this candidate's manual half proposes is already in `src/loop/wait.ts` as the shim's third positional argument (`limit=${3:-300}`). An instrument asserting that would pass on arrival and measure nothing. This test is scoped to the liveness verdict alone.
