---
type: Assumption
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Replay a denied call and a tool error and check they land as different records]]

Feasibility. Recording refusals separately assumes the two are separable at the point of capture. The usage channel currently counts both as "failed calls" — the 2026-08-05 trace reports 1 failure and shows it as an `ost_read_repo` error message. If a denial arrives looking like any other error string, the classifier is pattern-matching on host wording, which changes without notice and would make the channel quietly wrong rather than absent.
