---
type: Solution
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A session that dies before making any commit-worthy write is rare enough not to matter]]

Rather than a separate log or task list, carry the session id through into commit metadata (trailer or branch name) for every write the session makes. The next pass reconstructs exactly what an interrupted session touched by querying git for commits tagged with its id — no new state to keep in sync, since it rides on writes that already happen and already auto-commit.

**Compared to the alternatives.** Needs no new file the session has to remember to update, and can't drift out of sync with what was actually written the way a self-reported task list can. Tells the next pass *what changed*, not *what was intended but never finished* — a session backgrounded before writing anything at all leaves no trace under this scheme, unlike the checkpoint-log candidate.

## Issues
- 2026-08-17 Assumption surfaced ("A session that dies before making any commit-worthy write is rare enough not to matter") but its test is not created: settling it needs a count of how often interrupted sessions have zero committed writes, which this pass has no data source for. Left for an attended pass or human to design against real session history.
