---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[Nonzero exit code and failure summary when a pass errors]]
[[Status and digest lead with the last failed run]]
[[Supervisor heartbeat consumes run journals and alerts on error]]

**The need (operator's voice):** "P2_map died on an auth error and still exited 0, wrote a commit, and printed a tidy summary. If that had been my nightly cron, it would no-op forever while looking perfectly healthy."

**Why it matters:** unattended operation stands or falls on failure being *visible to machines*. The run journal records the error faithfully — but nothing that schedules, monitors, or alerts reads prose. Observed mechanically 2026-07-25T02:00:38Z (exit 0, commit 8038dfe9, error in `.ost-agent/runs/…P2_map.json`).

**Litmus (more than one way?):** yes — exit codes, status surfacing, supervisor-consumed journals, push alerts are all distinct answers.
