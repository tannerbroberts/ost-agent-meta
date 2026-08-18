---
type: Solution
source: 'INBOX:2026-07-24-friction-a-backgrounded-session-leaves-no-marker-of-where.md'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Sessions update the task list as they go, not only at a clean end a backgrounded session never reaches]]
[[A task list a prior session left behind saves more than it costs, and won't get acted on when stale or wrong]]

Have each session maintain a structured task list (done / in-progress / not-started) in a known location, updated as it works rather than only at the end. If backgrounded or interrupted, whatever it last marked in-progress is exactly the boundary the next pass needs, without inferring it from raw transcript events.

**Compared to the alternatives.** Gives the next pass structured, per-item status rather than a single last-action timestamp — more useful when a session was mid-way through a multi-step plan. Depends on the agent itself keeping the list current, so a session that dies mid-step without ever marking that step in-progress leaves the same gap this opportunity describes, just narrower.

## Issues
- 2026-08-17 Assumption surfaced ("Sessions update the task list as they go, not only at a clean end a backgrounded session never reaches") but its test is not created: this is a usability/behavioral question best answered by observing real sessions rather than a mechanical spec. Left prose-only for an attended pass or human to design.
