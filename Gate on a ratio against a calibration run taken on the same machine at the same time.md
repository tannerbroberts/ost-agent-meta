---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

The gate stops measuring milliseconds and starts measuring a ratio. Immediately before the real measurement, the same run executes a small fixed workload of known cost — the calibration — on the same machine under the same load. The gate compares the measurement to the calibration. A machine that is twice as busy makes both numbers twice as large and the ratio unchanged.

This is what makes the gate a statement about the code rather than about the afternoon it ran in.

**Compared to the alternatives.** Handles the exact failure named in the opportunity and needs no history, so it works on the first run and on a machine never seen before. It costs a little time on every run to produce the calibration, and it depends on the calibration workload degrading the same way the real one does under load — which is true for CPU-bound work and much less true once disk or network is involved.

**What would make this the wrong pick.** If the thing being measured and the calibration respond differently to contention, the ratio drifts for reasons that have nothing to do with the code, and the gate is now failing unpredictably instead of predictably. That would be a worse position than the absolute number, which is at least wrong in a direction people understand.
