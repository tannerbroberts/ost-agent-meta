---
type: Solution
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators would proactively check a rolling friction trend rather than needing to be pushed a per-run alert]]

Neither a single run's count nor a one-off spike says whether things are getting better or worse. Instead, track tool_error/retry counts across the last N firings and surface the trend — is friction climbing, flat, or falling — the next time the operator checks in, rather than at any one run's end.

**Compared to the alternatives.** This is the only candidate built to catch slow drift: a series of runs each just below any sane per-run threshold would sail past the alert-on-threshold design but show up plainly as a rising line here. It costs the operator nothing per run — there is nothing to read until they choose to look.

**What would make this the wrong pick.** It cannot tell the operator about one specific bad run they might want to investigate right now — by the time it shows up in a trend, the session that caused it is old news. It also needs enough history (several firings) before the trend means anything, so it is dead weight on a fresh or lightly-used vault.
