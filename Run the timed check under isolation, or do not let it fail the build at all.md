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

## Definition of done

[[Count how many timed checks would run somewhere that cannot guarantee isolation]]

```
npx vitest run test/release/timed-check-isolation-share.test.ts
```

Green means at least half of timed-check runs happen somewhere isolation can actually be guaranteed — a census over every place checks run (local machine, CI, scheduled pass, contributor machine), weighted by how often they really run there rather than counted per-location. It is red today because nothing enumerates the run locations or joins them to the run-frequency records.

**Why the share decides whether to build this at all.** The solution's second clause — *or do not let it fail the build* — converts a check into an advisory number wherever isolation cannot be promised. If most runs happen in those places, nearly every timed check becomes advisory, and an advisory number that cannot fail anything gets scrolled past for months while the regression it watched for arrives. That outcome is worse than the flaky gate it replaced, and it is invisible until someone counts.

**Weighting by run frequency, not by location count, is the load-bearing detail.** Four locations of which three cannot isolate sounds like a failure; if 90% of runs are in the fourth, it is a pass. A per-location count would give the wrong answer in exactly the case that matters.

**What green does NOT settle,** in the node's own words: it counts runs, not importance. The one place isolation is impossible might be where regressions are most likely to be introduced — a contributor's machine is the obvious candidate — and a share alone cannot show that. A green here should not be read as "the gate is safe", only as "the gate still gates most of the time".
