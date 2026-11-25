---
type: Solution
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Operators would proactively check a rolling friction trend rather than needing to be pushed a per-run alert]]

Neither a single run's count nor a one-off spike says whether things are getting better or worse. Instead, track tool_error/retry counts across the last N firings and surface the trend — is friction climbing, flat, or falling — the next time the operator checks in, rather than at any one run's end.

**Compared to the alternatives.** This is the only candidate built to catch slow drift: a series of runs each just below any sane per-run threshold would sail past the alert-on-threshold design but show up plainly as a rising line here. It costs the operator nothing per run — there is nothing to read until they choose to look.

**What would make this the wrong pick.** It cannot tell the operator about one specific bad run they might want to investigate right now — by the time it shows up in a trend, the session that caused it is old news. It also needs enough history (several firings) before the trend means anything, so it is dead weight on a fresh or lightly-used vault.

## Issues
- 2026-11-25 2026-11-24 unattended sweep, repo sight held: examined for a missing instrument and deliberately left without one. The only belief beneath it, "Operators would proactively check a rolling friction trend rather than needing to be pushed a per-run alert", is desirability about one operator's habit, and its test, "Ask the operator whether they'd check a rolling trend view unprompted, or need it pushed like an alert", is an ask whose measurement is the operator's answer. A spec could prove a trend renders; it could not prove anyone visits it, and no feasibility belief is stated on this node for a spec to hang from. What a human should do: set the lane with `ost-agent lane --set`, since `ost_flag_humans_required` is withheld on this surface. Not a skipped step; written so the next firing reads the verdict here instead of re-deriving it.
