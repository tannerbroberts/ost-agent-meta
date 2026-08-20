---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A create-time refusal can name the failing field without the tool body being restructured]]

**Variation dimension: who does the work — the tool carries the diagnosis.** Every refusal `ost_create_node` emits for an AssumptionTest names the field that actually failed its check (`threshold`, `instrument`, `humansRequired`) and states the form that would pass — "threshold must carry a numeric bar, e.g. 'at least 5 of 20'" — so the caller's retry is a lookup, not a guess. The session changes nothing about how it composes calls; the message does the work the session was doing by trial.

**Compared to its siblings.** The cheapest change in code and the one that leaves every rule exactly where it is: only the sentence changes. It is also the one that does least for a session that does not read past the first line of an error, and it fixes each misleading message only when somebody notices it is misleading — the observed instance was found by trial, and the next one would be too.

**What would make this the wrong pick.** If the check that fired is genuinely about the instrument *given* the threshold (a no-spec instrument is allowed only when a numeric bar exists), then a message naming one field is still half the truth; the honest sentence names the pair, and a builder has to decide whether that is clearer or just longer.

⚠️ Unvalidated. Agent-ideated from one recorded session.
