---
type: Assumption
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**Kind: feasibility.**

**The belief, stated so it could be false.** This candidate assumes the field can be added to a response that is already being truncated. `ost_next_work` currently caps four lists at 25 entries and reports 337 tests, 78 evidence items and 62 solutions behind those caps. A per-test command string is not free, and if adding it pushes more of the actual work list behind the cap, the pass gains a field and loses entries — which is a worse trade than the problem it fixes.

**What would make it false.** Carrying the field forcing any currently-visible list entry out of the response, or requiring the cap to drop below 25.
