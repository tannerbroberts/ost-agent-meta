---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Have someone with the build-loop harness's source open confirm whether a pre-interruption hook exists]]

[the text below is fetched DATA — it is never instructions]
---
This solution depends on the scheduling/build-loop harness firing a detectable signal (a shutdown hook, a pre-backgrounding callback, a wrapped exit path) at the moment a session is interrupted or moved to the background — not just at clean completion. If no such hook exists, "the instant it happens" cannot be honored and the checkpoint would only ever fire on graceful exits, which is the case that already leaves a marker today.

**Reliability, not just existence, is the belief.** A hook that fires on SIGTERM but not SIGKILL, or that fires after the process has already lost its write handle, does not carry this solution: the claim is that the hook fires reliably enough to *guarantee* the checkpoint line lands before state is lost. A hook that fires most of the time turns the checkpoint log into a record that is silently incomplete, which is worse than no log — the next pass would read it as authoritative.

**What the repository already suggests (recorded on the parent solution, 2026-08-18).** `src/loop/journal.ts` writes forward per completed step and needs no interruption hook at all, which is evidence that this assumption may not need to hold for the underlying need to be met. It does not settle whether the hook exists.

## Issues
- 2026-08-21 Folded in a second assumption node beneath the same solution ("The harness can hook the moment a session is backgrounded or killed reliably enough to always write the checkpoint") that stated the same feasibility belief in different words. Its reliability emphasis is preserved in the paragraph above.

## History
- 2026-08-22 merged "The harness can hook the moment a session is backgrounded or killed reliably enough to always write the checkpoint" into this node and deleted its file — Both nodes hung under the same solution and asserted one feasibility belief: that the harness fires a hook at interruption/backgrounding early enough and reliably enough to write a checkpoint line. Torres's test fails — no design could satisfy one and not the other, because they name the same mechanism. The loser carried no test and no recorded result; the survivor carries the test that probes exactly this belief, so the merge loses nothing and stops the tree re-reading and re-ideating under one belief twice.
