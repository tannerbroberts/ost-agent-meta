---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
instrument: npx vitest run test/loop/wait-expiry-utility-availability.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility**, and it is the one that could kill the parent candidate outright.

**Pre-committed threshold:** `timeout` resolves and runs when invoked the way the shim would invoke it — from plain POSIX `sh`, with no Homebrew prefix assumed and no `gtimeout` fallback — on the platform the build loop actually fires on. Anything short of that is a refutation, not a partial pass: a dependency that resolves only after an install step is exactly the "command not found three weeks later" failure `src/loop/wait.ts` argues against at length, and it reads to the composer as the affordance never having existed.

**Why this is worth a spec rather than a shrug.** The parent candidate's whole position is bought-not-built: it inherits exit status 124, the bound argument, the signal handling and a man page nobody here maintains. All of that is worth having and none of it is reachable if the binary is absent. The candidate's own prose already concedes that `timeout` is GNU coreutils, that stock macOS ships it only as `gtimeout` via Homebrew, and that the machine is a Mac. This test turns that concession from an argument into a result.

**The assertion the builder has to write.** Install the rendered shim into a temp dir and execute a resolution probe through the same `execFileSync("sh", …)` path the existing suite already uses in `test/loop/wait-primitive-affordance.test.ts`, then assert the utility both resolves and returns its documented expiry status on a condition that never holds. Running the probe through the test runner's own environment instead would pass on a developer machine with Homebrew on `PATH` while the unattended firing's environment lacks it — that is the trap this spec exists to avoid, and it is the difference between measuring the shim's world and measuring the author's.

**Honest label on the red: `no-spec`, the weak kind.** The named file does not exist, so the command fails identically to any other question written on that path. The stronger form was refused — instruments are argv-only, so a name filter against the existing spec file is not expressible — and this pass may not write code. It is also worth saying that `renderWaitShim()` today contains no `timeout` invocation at all (the give-up is a `while` loop with a `waited` counter), so even once the file exists the assertion stays red until the shim actually reaches for the utility.

**What a green run does NOT settle.** Availability only. It says nothing about whether inheriting 124 is a convention this project's callers will read correctly, whether the operator wants an external dependency at all, or how the candidate degrades on a machine where the binary later disappears.
