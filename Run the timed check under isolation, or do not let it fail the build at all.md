---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Count how many timed checks would run somewhere that cannot guarantee isolation]]

Stop trying to make the measurement robust to contention and remove the contention instead. Timed checks run only where load is controlled — a dedicated runner, a quiet queue, one at a time. Anywhere that guarantee does not hold, the check still runs and still reports its number, but it cannot fail anything; it is recorded and shown, never gating.

The principle is that a check which fails for reasons unrelated to the change is not a weak check but a harmful one, because the correct response to it is to rerun until it passes, and that habit is what eventually lets a real regression through.

**Compared to the alternatives.** The only option that fixes the cause, and it makes the number mean what it says without statistical machinery or a calibration workload. It also costs infrastructure that a laptop-based project does not have, and it gives up gating in most of the places the check will actually run — which is a real reduction in coverage, chosen deliberately over a gate that lies.

**What would make this the wrong pick.** Advisory checks get ignored. A number that appears in output and cannot fail anything will be scrolled past for months, and the regression it was watching for will arrive during that time with nothing to stop it.
