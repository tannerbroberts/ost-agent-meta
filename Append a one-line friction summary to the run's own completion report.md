---
type: Solution
source: 'agent-ideated:2026-08-17-unattended-sweep'
created: '2026-08-17'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Whatever channel already tells the operator a run finished (a commit message, a status file, a completion note) gets one more line: how many tool_error / retry events this run hit. No new surface, no new place to check — the friction count rides along with information the operator already reads.

**Compared to the alternatives.** Cheapest to ship: it is pure addition to an existing report, not a new mechanism. It is also the easiest to ignore — a number appended to a report the operator already skims is exactly as visible as everything else in that report, no more.

**What would make this the wrong pick.** If operators do not actually read the completion report (they read status only through a different surface), the line goes unseen. It also gives no signal across runs — five roughs sessions in a row would each report quietly and never sum to a pattern the operator notices.
