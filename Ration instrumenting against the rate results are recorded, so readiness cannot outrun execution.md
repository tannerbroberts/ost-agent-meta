---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check the instrument allowance holds at the floor while no result has ever been recorded]]

**The mechanism: backpressure.** A pass may attach instruments only up to some multiple of the results actually recorded since the last one. With zero results ever recorded, the allowance is a small fixed floor — enough to keep working, not enough to instrument another eighty-eight in a day. When results start being recorded, the allowance opens up in proportion.

**Why this shape.** It treats the imbalance as a flow problem rather than a capability gap, and it is the only candidate that needs nothing new to be built on the execution side. It also fails safe: if nobody ever records a result, the tree stops accumulating readiness instead of accumulating it forever, and the stall becomes visible immediately rather than after 255 tests.

**Compared to its siblings.** Cheapest by a wide margin — a counter and a refusal at the write boundary, no runner, no new evidence-handling. It is the only one that changes an agent's behaviour rather than its bookkeeping or its tooling. Against that, it is the only candidate that makes the tree *worse* in the short run on purpose: it deliberately withholds useful work to make a shortage legible, and if the operator's constraint is genuinely their own hours, refusing to prepare work for them does not give them any hours back. It is a forcing function, and forcing functions applied to a bottleneck nobody can widen are just friction.

**What would make this the wrong pick.** If instrumenting is the cheap, valuable half and executing is genuinely blocked on something structural — a permission, a missing runner, a person's availability — then rationing punishes the part that works to protest the part that does not. Worth weighing against [[A runner that executes instruments and records exit codes only, judging nothing]] specifically: if that ships, this becomes unnecessary; if it cannot ship, this becomes the honest response.

⚠️ Unvalidated. Agent-ideated on 2026-08-05.

## Definition of done

[[Check the instrument allowance holds at the floor while no result has ever been recorded]]

`npx vitest run test/ost/instrument-rationing.test.ts`

With zero recorded results the allowance stops at a non-zero fixed floor and further instrument calls are refused with a reason that names the shortage rather than a generic error; each recorded result raises the allowance in proportion. Red today because nothing rations. The spec can prove the valve opens and closes correctly and cannot tell whether a valve was the right thing to install.
