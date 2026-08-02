---
type: Opportunity
status: unvalidated
source: >-
  INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-once-ost-next-work.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

A wall-clock budget test failed at 2004ms against a hard 2000ms bar while running inside the full suite, then passed by an enormous margin seconds later when run on its own. No code changed between the two runs. The threshold is an absolute millisecond count with no tolerance for the CPU contention that a shared sandbox guarantees, so the suite can convict a build that is not guilty.

The damage is to the gate's standing rather than to the build. A bar that can fail for reasons unrelated to the code teaches everyone to re-run it and move on, which is precisely the habit that lets a real regression through the next time. A four-millisecond overshoot cannot be told from a genuine slowdown by looking at the result.

**The need:** I want a performance bar that fails when the code got slower and not when the machine got busy.

More than one way to address this: measure relative to a baseline captured in the same run, re-run a breached budget in isolation before failing, budget against CPU time rather than wall clock, or widen the bar and track the trend instead of a single threshold.

## Provenance

Distilled from `INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-once-ost-next-work.md` — filed by the loop on the twentieth scheduled pass, running the gates against the meta vault. Recorded at `assertion`: the inbox channel's earned ceiling.

## Issues
- 2026-08-02 Likely merge candidate — flagged by the pass that created it. This node was created to map `INBOX:friction/2026-08-01-friction-wall-clock-budget-test-flaked-once-ost-next-work.md`, but its parent "A test that failed because the machine was busy looks exactly like one that failed because I broke something" already carries the three solutions this node's own body proposes: "Budget against a same-run baseline instead of against the clock", "Assert on work units instead of milliseconds", and "Re-run once and report the disagreement rather than the first result". The parent also already has the assumption test "Check whether isolation correctly acquits a flake and convicts a real regression". So the distinction between parent and child is thin: the parent is the general inability to tell a flake from a regression, this child is the specific mechanism (an absolute threshold) by which that happens. A human may well decide this should be folded into the parent as corroborating evidence rather than kept as a separate branch. No solutions were ideated here on purpose, to avoid duplicating the parent's three.
