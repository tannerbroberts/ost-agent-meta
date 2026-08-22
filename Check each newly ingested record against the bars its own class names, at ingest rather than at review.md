---
type: Solution
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A bar can be stated as a pattern and a count over one arriving record, so ingest can judge it without a model]]
[[Claims on this tree go stale mostly because a new record arrived, not for reasons ingest never sees]]

**Variation dimension: when it acts — this candidate moves the check to the moment new evidence arrives, not to a cadence and not to a read.** `ost_ingest_inbox` already touches every new record exactly once, at the only moment the vault is guaranteed to be looking at it. A bar declares the record shape it is counted over (here: transcript friction lines matching `permissions to use mcp__`); ingest matches each captured record against the registered bars, and a record that breaches one is reported in the ingest output beside the capture line — "captured 1 from transcript; `TRANSCRIPT:90d8aeae` breaches the bar on 'The unattended run is scoped for tools nobody granted it' — 8 denials, bar is at most 1."

The regression this node is distilled from would have been named at 2026-08-17, in the firing that ingested it, rather than found by hand on 2026-08-21.

**Compared to its siblings.** The only candidate with no latency at all: the other two surface a breach when someone next reads the node, which is exactly the event that did not happen for four days. It is also the only one that needs no re-count of the corpus — it tests one arriving record against a threshold, which is O(1) per capture rather than a sweep over every record ever held.

**What it deliberately gives up.** It can only catch breaches that arrive *as new records*. A bar broken by something the vault does not ingest — a config change, a shipped code change, a claim that was wrong the day it was written — is invisible to this candidate and stays invisible. It is a tripwire, not an audit.

**What would make this the wrong pick.** If most stale claims on this tree turn out to have decayed without any new record arriving, the tripwire fires on the minority of cases and the operator still cannot trust an unflagged claim. That is a measurable question about this vault's own history and it should be answered before this is built, not after. It also puts judgement into the ingest path, which today is deliberately dumb: a false breach report at ingest is noise on the one surface every pass reads first, and enough of it would train passes to skim the ingest output — the failure mode that made this need invisible in the first place.

⚠️ Unvalidated. Agent-ideated from one recorded session.
