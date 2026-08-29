---
type: Opportunity
source: 'TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d'
created: '2026-08-29'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Remove the wait have the work the firing started announce its own completion]]

**The need (operator's voice):** "My unattended run waited, gave up, and told me the same thing it would have told me if the thing I was waiting for were never going to happen. So it waited again. Twenty minutes of a firing I am paying for went into learning nothing."

**What was observed.** `TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d`, an unattended firing captured 2026-08-29 (mirrored 0d ago), produced 9 friction events. Four of them are the same line:

- `Exit code 1 … await: gave up after 300s; the condition still exits 1.` ×4
- plus two `retry` events re-issuing the identical wait — `await 'grep -qE "Test Files.*\(" /tmp/ost-suite-full.txt'` and the same against `/tmp/ost-suite-quiet.txt`, each carrying `timeout: 600000`.

The session was waiting for its own test suite to finish writing a results file. It gave up, re-issued the same wait unchanged, and gave up again. Two conditions, four expiries, roughly twenty minutes.

**The mechanism, read first-party out of the code rather than inferred.** `renderWaitShim` in `src/loop/wait.ts` ends its loop with `exit "$rc"`, and its own doc comment states the design: "The exit status is the condition's own, and giving up says so on stderr rather than looking like success." So an expiry and a condition that is simply false exit identically. `DEFAULT_FOR_SECONDS` is 300 and is applied when the caller names no third argument — which none of the observed calls did, so the wait gave up at half the 600s the caller had allotted the Bash call, on a bound the call site never mentions. `test/loop/wait-primitive-affordance.test.ts` pins the current behaviour explicitly: `run(["exit 3", "1", "2"])` asserts `status` is `3`, the condition's own code.

**Why it matters.** The give-up carries no evidence of progress. Nothing in it says whether the condition's output changed between the first attempt and the sixtieth, so the caller cannot distinguish "the suite was three seconds from finishing" from "the file will never exist". Re-issuing the identical wait is the rational move under that ambiguity, and it is also the expensive one — and it happens with nobody watching, which is the condition under which a wrong guess costs a whole firing rather than a shrug.

**Distinct from its neighbours, by Torres's test.** Against "One red run is all I get, and nothing in it separates noise from a real break": a solution that makes a wait report whether its condition moved between attempts addresses this node and does nothing for a flaky perf gate, and re-run-and-compare addresses that sibling and nothing here. Against "A refusal names a field that was fine, so the retry fixes the wrong thing": that node is about a message that misdirects a retry with wrong information; this is about a message that cannot direct one at all, plus a bound the caller did not choose. Both pass.

**Litmus test (more than one way to address?):** Yes — give expiry a reserved exit status distinct from any condition's, the way `timeout(1)` uses 124; report the attempt count, elapsed time and whether the condition's output changed; make the bound explicit at the call site or inherit the caller's own timeout instead of defaulting under it; block on the job's exit rather than polling for its artifact. Real trade-offs between them. Passes.

**Evidence rung:** `observed` — the source is a mechanical capture of the agent's own session, not a recalled account. It observes this product's own runs rather than an outside user, so it grounds usability and says nothing about whether anyone else wants this.

_Source: `TRANSCRIPT:cf2cef94-0aee-4647-80e0-9d64dbe0e18d` via `ost_next_work`, plus first-party reads of `src/loop/wait.ts`, `test/loop/wait-primitive-affordance.test.ts` and `examples/automation/build-pass.sh` through `ost_read_repo`. No test was run and no result is recorded._
