---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Have someone with the tool harness open confirm self-created files can be tracked distinctly from pre-existing ones within a session]]

Skipping the guard only for self-created files is safe only if the harness can distinguish "this session's Write tool created this file earlier in this same session" from "this file already existed and the session just hasn't read it yet" — reliably enough that a pre-existing file can never be misclassified as self-created and slip past the guard unread.
