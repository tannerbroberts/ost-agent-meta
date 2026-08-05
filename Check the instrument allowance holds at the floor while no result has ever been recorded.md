---
type: AssumptionTest
created: '2026-08-05'
evidence: assertion
threshold: >-
  With zero recorded results the allowance stops at the fixed floor and further
  instrument calls are refused with a reason naming the shortage; each recorded
  result raises the allowance in proportion.
instrument: npx vitest run test/ost/instrument-rationing.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption: backpressure can be applied at the write boundary without wedging the tree.** A ration that refuses everything leaves a pass unable to do any useful work; one that never binds is decoration. The claim is that a fixed floor plus a proportional allowance sits between those.

**Risk category: feasibility.**

**Design.** Against a vault with zero recorded results, assert instrument calls succeed up to the floor and are then refused with a reason that names the shortage rather than a generic error — the refusal has to be legible or it will read as a bug. Record a result and assert the allowance rises proportionally. Assert the floor is never zero, so a fresh vault can still be worked.

**Why it is small.** A counter and a refusal, exercised over a fixture vault.

**What it does NOT cover — and it is the objection that should probably decide this node.** Whether withholding work helps. If execution is blocked on something structural rather than on anyone's willingness, rationing punishes the half that works to protest the half that does not, and the operator whose hours do not exist gets no hours back. A spec can prove the valve opens and closes correctly; it cannot tell whether a valve was the right thing to install. That judgement belongs with the sibling comparison against [[A runner that executes instruments and records exit codes only, judging nothing]].
