---
type: Solution
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Have the harness itself (not the agent, which may not get a final turn) append one line to a fixed-path log the moment a session is backgrounded or its process ends: session id, timestamp, and the last tool call it completed. The next pass reads this log first, before re-deriving state from the transcript or the tree.

**Compared to the alternatives.** Cheapest and most reliable because it's written by the harness rather than relying on the agent to notice it's about to be interrupted and self-report — the exact failure mode the founding evidence describes (an earlier pass had no way to tell what it had finished). Only records a timestamp/last-action marker, not a structured account of what's done vs. abandoned.
