---
type: AssumptionTest
source: 'REPO:OST-Agent/src/loop/wait.ts'
created: '2026-10-02'
evidence: assertion
threshold: >-
  at least 1 second invocation on an identical never-true condition reports a
  prior spend of >= the first run's bound and gives up only after >= 2x that
  bound
instrument: npx vitest run test/loop/wait-escalation.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec asserts.** Install `renderWaitShim()` into a temp dir with mode `0o755`. `test/loop/wait-primitive-affordance.test.ts` already does exactly this with its `installShim()` and `run()` helpers, so they can be reused or lifted. Then run the shim twice on one never-true condition (`false`) with a small interval and bound, for example `await 'false' 1 2`, and assert:

1. The first run exits non-zero, and its stderr names the bound it spent (`gave up after 2s`). This already passes today; it is the control.
2. The second, identical invocation's stderr names the time already spent by the first (≥ 2s) **and** gives up only after a bound of at least double the first (≥ 4s of its own waiting). This is the assertion that is red today: the shim sets `waited=0` on every run and writes no record, so the second run reports exactly what the first did.
3. Once the hand-set ceiling is reached, a further identical invocation refuses before waiting and names the accumulated total.
4. The existing contract is unchanged: exit 0 on a true condition, exit 2 with no condition.

**Honest grade of this instrument: weak today, by its own label.** `test/loop/wait-escalation.test.ts` does not exist yet, so the command currently fails as `no-spec`. It would fail that way whatever question was written here, it mints no build permit, and it does not count as the red this test needs. This surface cannot write a spec file. A builder's first job is to write assertions 1–4 above, after which the command should fail on assertion 2 against today's shim. That is the specific red this test is designed to produce. If assertion 2 passes the moment the file exists, the instrument is wrong and should be replaced, not celebrated.

**What this does NOT settle.** Only feasibility: that the shim *can* carry the record. It says nothing about whether escalating is wise. That question is "Count the recorded expiries that later succeeded against those whose condition could never have become true", which stays humans-required. It also says nothing about the key-defeat problem the solution's prose records: a caller that renames its output file between attempts still gets a fresh 300s, and a green here does not fix that.
