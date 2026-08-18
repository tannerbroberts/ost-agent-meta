---
type: Solution
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The harness can hook the moment a session is backgrounded or killed reliably enough to always write the checkpoint]]
[[The harness exposes a hook at the moment a session is backgrounded or interrupted, in time to write one line before control is lost]]

Have the harness itself (not the agent, which may not get a final turn) append one line to a fixed-path log the moment a session is backgrounded or its process ends: session id, timestamp, and the last tool call it completed. The next pass reads this log first, before re-deriving state from the transcript or the tree.

**Compared to the alternatives.** Cheapest and most reliable because it's written by the harness rather than relying on the agent to notice it's about to be interrupted and self-report — the exact failure mode the founding evidence describes (an earlier pass had no way to tell what it had finished). Only records a timestamp/last-action marker, not a structured account of what's done vs. abandoned.

## Issues
- 2026-08-17 Assumption surfaced ("The harness can hook the moment a session is backgrounded or killed reliably enough to always write the checkpoint") but its test is not created: this is a feasibility question about the harness's own lifecycle hooks, and this unattended sweep holds no `ost_read_repo` grant. Needs an attended pass with repo sight to write the spec-file instrument.
