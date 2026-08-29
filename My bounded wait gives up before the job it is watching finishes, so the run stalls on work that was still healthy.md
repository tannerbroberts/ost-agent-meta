---
type: Opportunity
source: 'TRANSCRIPT:2a686fb9-1bf7-4f01-b2f9-b66c8aea20ef'
created: '2026-08-29'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Delete the wait let harness-tracked work announce its own completion instead of being polled]]
[[Automate the liveness verdict, leave the spend ceiling to the caller]]
[[Adopt the platform's own job-control wait instead of maintaining a bespoke shell helper]]

**The need (operator's voice, inferred from observed behavior):** "I started a long job in the background and used the waiting primitive I was told to use. It gave up while the job was still perfectly healthy, and what came back told me only that the condition was still false — not whether the thing I was waiting for was running, dead, or nearly done. So the run stalled, and I could not tell that it had."

**What was observed.** Session `TRANSCRIPT:2a686fb9-1bf7-4f01-b2f9-b66c8aea20ef` (2026-08-28, unattended, nobody watching) produced 20 friction events, of which **nine are the same failure**: `Exit code 1 await: gave up after 300s; the condition still exits 1.` The conditions were ordinary and correctly composed — `await 'grep -q "Test Files" /tmp/suite-baseline.txt'`, `await 'grep -q "wall-clock-budget" /tmp/suite-baseline.txt'`, `await 'grep -q "Test Files" /tmp/suite-final.txt'` — each waiting on a full vitest suite to write its output. Four of the nine were immediately re-issued as retries with `timeout: 500000` set on the tool call, which had no effect: the 300s cap belongs to the helper, not to the tool timeout the caller can set. The session spent roughly forty-five minutes of wall clock on expired waits and never learned whether the suite was alive.

**Why this is not the Monitor-refusal need beside it.** "The Monitor tool refuses the exact commands an unattended run needs to check on its own background work" is about commands being *rejected at composition time* — command substitution, chained parts, a path outside the working directory. This node is the opposite situation: the command was **accepted and ran exactly as designed**. `await` is itself the sanctioned correction this workspace issues for those refusals ("To wait for a condition, use Monitor with an until-loop... `await '<condition>'` is on this session's PATH"), and it carries a fixed 300s give-up. So the remedy for the refusal need produced this one. A pass that fixed every Monitor grammar refusal would leave all nine of these failures exactly as they are.

**Why it is not the noise-vs-break need either.** "A test that failed because the machine was busy looks exactly like one that failed because I broke something" is about a *verdict* that cannot be attributed once it arrives. Here no verdict ever arrived: the wait expired without the measurement being taken. The overlap is real but partial — both leave the reader unable to attribute an exit code — and the distinguishing fact is that this one has no result to attribute, only an absence.

**Litmus test (more than one way to address it?):** Yes, and they trade off against each other. The bound could be caller-settable, so the waiter declares how long the job plausibly needs. The wait could report *liveness* — is the process still running? — as a third outcome distinct from both success and expiry, so "not yet" and "never" stop sharing an exit code. It could wait on process exit rather than on a marker appearing in a log, removing the guess about what string signals completion. The job could emit a heartbeat the wait consumes, so a slow-but-advancing run is distinguishable from a wedged one. Or expiry could return the job's current partial output rather than only the condition's exit status. Passes.

**What this node does not claim.** Whether 300s is the wrong number is not the need — a longer fixed cap would have failed the same way against a suite that takes longer still. The need is that the waiter cannot express how long its work needs and cannot learn, on expiry, whether waiting longer would have helped.

**Evidence rung:** `observed` — captured mechanically from the agent's own session transcript, not recalled afterwards. It grounds usability, not desirability: it is this product's own agent hitting the limit, not an outside user reporting demand. One session, nine occurrences; a second independent session would strengthen it and none is on record yet.

## Correction to this node's own framing, from repo sight (same firing, 2026-08-28)

The prose above closes with: *"The need is that the waiter cannot express how long its work needs."* **That is wrong, and it is worth correcting in place rather than leaving for a later pass to trip over.** Read first-party this firing via `ost_read_repo` against `src/loop/wait.ts`, which is this product's own module — the `await` shim is shipped from here, not by the harness.

**The bound is already caller-settable.** The shim's usage line is `await '<condition>' [seconds-between-attempts] [give-up-seconds]`, and its body reads `limit=${3:-300}`. A caller who wanted twenty minutes could have written `await 'grep -q "Test Files" /tmp/suite-baseline.txt' 5 1200` and the nine expiries would not have happened. `DEFAULT_FOR_SECONDS = 300` is a default, not a cap.

**So the real need is narrower and much cheaper: the affordance that teaches the form does not mention the argument exists.** `renderWaitAffordance()` in the same file is what reaches a session — this firing's own workspace correction block reproduces its output verbatim. It emits three lines of explanation and three worked examples, and **every example is the one-argument form**. The only mention of the bound is the phrase "gives up after 300s rather than hanging", which reads as a property of the tool rather than as a default a caller may override. Nothing in what a composing session sees says there is a third argument.

**The observed session's behaviour is exactly what that omission predicts.** It reached for a longer bound — four of the nine failures were immediately re-issued with `timeout: 500000` on the `Bash` call — and reached for the wrong knob, because the right one had never been shown to it. That is not a session failing to read documentation; the documentation it was given omits the field. A run then spent roughly forty-five minutes expiring against a default it did not know was a default.

**What this does and does not change.**

- The *stalling* half of this node stands, and the evidence is unchanged: nine expiries, one session, work still healthy.
- The *cause* changes from "no way to express duration" to "the way to express duration is undisclosed at the point of use", which is a documentation-adjacent defect in `renderWaitAffordance()` and cheap.
- The *liveness* half stands entirely and is untouched by any of this. Even with a correct bound, expiry still cannot distinguish "still running" from "dead" — the shim reports the condition's own exit status and nothing about the job. A caller who sets 1200s and expires anyway learns exactly what this session learned.
- The candidate "Automate the liveness verdict, leave the spend ceiling to the caller" is **half already shipped**: its manual half — the caller-declared ceiling — exists. Its live half is the liveness verdict plus the disclosure. That candidate's assumption and test are written against the live half only, and an instrument asserting the ceiling is settable would pass today and therefore measure nothing.

**This is also an instance of a need already on this tree, one layer up.** "The agent has to guess what resources it's actually working with" records the general form: a capability exists, the agent has no declaration of it, and the cost is paid by discovery. Here the undeclared resource is an argument of a helper this same project ships, and the omission is in a string this project renders. Recorded here rather than duplicated there.

_First-party to this firing: `ost_read_repo` reads of `src/loop/wait.ts` and the `test/loop/` listing, against the observed session `TRANSCRIPT:2a686fb9-1bf7-4f01-b2f9-b66c8aea20ef`. Grounds feasibility and usability; says nothing about desirability. No test was run and no result is recorded._
