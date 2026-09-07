---
type: Solution
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
killIf: >-
  A gap of more than three cadences occurs, the liveness line renders correctly
  for it, and the operator still takes no action and never mentions it — the
  line was read and ignored.
killBy: '2026-11-07'
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: automated-vs-manual. Position taken: detection fully automated and nothing new stored; the only manual step left is that a person must eventually read a report.**

`ost_next_work` gains a `liveness` field beside its existing counters: time since the last recorded firing, the configured `loop.cadence`, and a flag when the observed gap exceeds some multiple of it. Every input already exists — `.ost-agent/usage/events.jsonl` carries a timestamp per invocation and `ost.config.yaml` declares the cadence — so this stores nothing, schedules nothing and adds no process. It is a computation over data the vault already holds, in the response the operator already reads.

**Why this position and not another.** The gap this node was mapped from was not hidden. It was sitting in three separate artifacts in this vault, in plain form, and the reason nobody saw it is that no surface put it beside the numbers people actually look at. Where the sibling above adds a new participant to detect the outage, this one asserts that no detection is needed at all — the record is already here and the defect is purely that nothing renders it.

**What it deliberately does not do.** It raises no alarm, sends nothing, and wakes nobody. It changes what a report says and nothing else.

**What it gives up, plainly, and this is the honest weakness.** It is strictly pull, and a dark loop generates no reports. If nothing fires, nothing calls `ost_next_work`, and the liveness line that would announce the outage is never rendered for anyone. It tells the operator who comes back and looks; it cannot tell the operator who has stopped looking, which is the operator most likely to have an unnoticed outage. Against the sibling above it is strictly weaker at detection and strictly cheaper and safer at everything else.

**One thing it does that the sibling cannot.** It works retroactively. The trace already holds the history, so on the day it ships it can state that a three-day gap occurred four days ago. A ping-based switch only ever knows about outages after it is installed.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-09-07; a human to review.
