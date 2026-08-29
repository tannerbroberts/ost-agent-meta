---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: >-
  exactly 1 of the 2 probed runs returns the reserved expiry status, and it is
  the run that expired
instrument: npx vitest run test/loop/wait-expiry-status.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** The parent solution's own sharpest-risk line says the belief worth testing is whether the distinction can be added without breaking what reads the status, and that is settled by code, not by anyone's afternoon.

**The two runs this test pins, and why it takes two.** One run is a condition that never holds until the bound expires — it must come back with the status reserved for expiry. The other is a condition that fails fast for its own reason within the bound — it must come back with *that* status, unchanged. A test that only checked the first would be satisfied by a shim that returned the expiry status for every non-zero outcome, which is the exact regression this change risks: collapsing two events into one in the opposite direction from today.

**Why it is not already true.** `renderWaitShim()` in `src/loop/wait.ts` ends `exit "$rc"` — the condition's own status — so expiry and condition-false are indistinguishable to any caller reading an exit code. The give-up line on stderr says `gave up after ${waited}s`, which is prose a human reads and a caller cannot branch on.

**The breakage this test is designed to surface, named so the builder finds it before CI does.** `test/loop/wait-primitive-affordance.test.ts` asserts today that `run(["exit 3", "1", "2"])` returns status `3` — a never-true condition returning the condition's own status. That is the old contract, stated as an assertion, and this change contradicts it. It has to be revised deliberately, with the revision recorded, rather than incidentally broken by a builder who reads a red suite as noise. Any other caller branching on the shim's status has to be found first; the repository's own corpus walkers are where to look.

**Honest label on the red: `no-spec`, the weak kind.** `test/loop/wait-expiry-status.test.ts` does not exist, so today's failure is the one any question written on that path would produce. The stronger form — an assertion filter against the existing spec file — is not expressible here, because instruments are validated as argv with no shell and quoted `-t` filters are refused. What the paragraphs above give the builder instead of a blank file: two named runs, the file and line of the assertion that must change, and the regression direction the second run exists to catch.

**What a green run does NOT settle.** That the reserved number is the *right* one — whether to borrow 124 from `timeout(1)` or pick a private status is the argument the sibling candidate carries, and this test is deliberately agnostic about which number is used. It also says nothing about whether any caller will ever branch on the distinction, which is a question about how the loop is written and not about what the shim can express.
