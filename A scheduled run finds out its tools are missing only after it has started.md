---
type: Opportunity
status: unvalidated
source: >-
  INBOX:friction/2026-08-01-friction-third-straight-scheduled-pass-15th-16th-17th-wit.md
created: '2026-08-02'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

Three scheduled passes ran in a session where the vault's tools were simply absent, so mapping, ideation and ranking could not run at all — only the command line remained. The run started, discovered its surface was empty, and each pass had to work that out for itself after the compute had already been committed.

The scheduling is the aggravating factor. An interactive session that loses its tools has a person present who sees it immediately; a scheduled one repeats the same discovery on a cadence, and the only record that anything went wrong is whatever the pass thought to file. Three identical passes is three identical discoveries and no accumulating signal.

**The need:** I want a scheduled run to know before it starts whether it can do the work it was scheduled for.

More than one way to address this: assert the required surface as a precondition and exit loudly, have the scheduler verify the environment before dispatching, fall back to the command-line path automatically when the tools are absent, or escalate after the first toolless run rather than the fourth.

## Provenance

Distilled from `INBOX:friction/2026-08-01-friction-third-straight-scheduled-pass-15th-16th-17th-wit.md` — filed by the session on the third consecutive toolless scheduled pass. Its root cause was located a day later and is mapped under a sibling opportunity. Recorded at `assertion`: the inbox channel's earned ceiling.
