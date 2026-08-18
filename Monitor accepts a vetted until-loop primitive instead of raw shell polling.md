---
type: Solution
source: 'TRANSCRIPT:0f28d01f-35fa-49f0-b085-89170e306ef8'
created: '2026-08-18'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Give Monitor a structured "wait for condition, then run a follow-up read" primitive — poll interval plus a bounded command, no shell substitution — so a run expresses "wait until this finishes" as a typed call Monitor already knows how to grant, rather than composing an until/sleep shell loop that trips the command_substitution refusal.
