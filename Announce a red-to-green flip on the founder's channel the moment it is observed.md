---
type: Solution
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Highlight interrupts keep their signal — the founder keeps reading them rather than tuning them out]]

When a post-build observation records an instrument going from red to green, send one short push message to a channel the founder already watches, at the moment the flip is recorded — the event, the solution it clears, and where the observation lives.

**Against the alternatives beside it:** this is the immediate, event-granular end of the spectrum. It needs no curation artifact and no digest cadence, and it surfaces the win while the context is fresh. Its risk is the known one recorded for block notifications — interrupts that arrive too often stop being read — and red-to-green flips are rarer than blocks, which is the reason to believe the risk is smaller here. It cannot surface opportunity-kill highlights, because those events do not occur without a human today.
