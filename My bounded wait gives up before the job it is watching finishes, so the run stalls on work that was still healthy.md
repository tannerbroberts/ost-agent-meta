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

**The need (operator's voice, inferred from observed behavior):** "I started a long job in the background and used the waiting primitive I was told to use. It gave up while the job was still perfectly healthy, and what came back told me only that the condition was still false — not whether the thing I was waiting for was running, dead, or nearly done. So the run stalled, and I could not tell that it had."

**What was observed.** Session `TRANSCRIPT:2a686fb9-1bf7-4f01-b2f9-b66c8aea20ef` (2026-08-28, unattended, nobody watching) produced 20 friction events, of which **nine are the same failure**: `Exit code 1 await: gave up after 300s; the condition still exits 1.` The conditions were ordinary and correctly composed — `await 'grep -q "Test Files" /tmp/suite-baseline.txt'`, `await 'grep -q "wall-clock-budget" /tmp/suite-baseline.txt'`, `await 'grep -q "Test Files" /tmp/suite-final.txt'` — each waiting on a full vitest suite to write its output. Four of the nine were immediately re-issued as retries with `timeout: 500000` set on the tool call, which had no effect: the 300s cap belongs to the helper, not to the tool timeout the caller can set. The session spent roughly forty-five minutes of wall clock on expired waits and never learned whether the suite was alive.

**Why this is not the Monitor-refusal need beside it.** "The Monitor tool refuses the exact commands an unattended run needs to check on its own background work" is about commands being *rejected at composition time* — command substitution, chained parts, a path outside the working directory. This node is the opposite situation: the command was **accepted and ran exactly as designed**. `await` is itself the sanctioned correction this workspace issues for those refusals ("To wait for a condition, use Monitor with an until-loop... `await '<condition>'` is on this session's PATH"), and it carries a fixed 300s give-up. So the remedy for the refusal need produced this one. A pass that fixed every Monitor grammar refusal would leave all nine of these failures exactly as they are.

**Why it is not the noise-vs-break need either.** "A test that failed because the machine was busy looks exactly like one that failed because I broke something" is about a *verdict* that cannot be attributed once it arrives. Here no verdict ever arrived: the wait expired without the measurement being taken. The overlap is real but partial — both leave the reader unable to attribute an exit code — and the distinguishing fact is that this one has no result to attribute, only an absence.

**Litmus test (more than one way to address it?):** Yes, and they trade off against each other. The bound could be caller-settable, so the waiter declares how long the job plausibly needs. The wait could report *liveness* — is the process still running? — as a third outcome distinct from both success and expiry, so "not yet" and "never" stop sharing an exit code. It could wait on process exit rather than on a marker appearing in a log, removing the guess about what string signals completion. The job could emit a heartbeat the wait consumes, so a slow-but-advancing run is distinguishable from a wedged one. Or expiry could return the job's current partial output rather than only the condition's exit status. Passes.

**What this node does not claim.** Whether 300s is the wrong number is not the need — a longer fixed cap would have failed the same way against a suite that takes longer still. The need is that the waiter cannot express how long its work needs and cannot learn, on expiry, whether waiting longer would have helped.

**Evidence rung:** `observed` — captured mechanically from the agent's own session transcript, not recalled afterwards. It grounds usability, not desirability: it is this product's own agent hitting the limit, not an outside user reporting demand. One session, nine occurrences; a second independent session would strengthen it and none is on record yet.
