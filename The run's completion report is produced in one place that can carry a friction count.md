---
type: Assumption
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[One completion path carries the run's friction counts, and a clean run says so explicitly]]

Feasibility belief, surfaced beside the desirability one rather than in place of it.

The sibling assumption ("Operators actually read the run's completion report closely enough to notice an appended friction line") is a person's answer and stays one. But this candidate's whole claim to being the cheapest option — "pure addition to an existing report, not a new mechanism" — rests on a mechanical premise nothing on the tree checks: that there IS one report, generated in one place, and that the friction count is already computable at the moment it is written.

Stated so it could be false: a single code path produces the completion an operator reads, and the tool_error/retry counts for that run are available to it without a new capture step. If the completion is actually assembled in several places — a commit message here, a state file there, a report the harness prints — then "one more line" is not one change, and the cheapness argument that makes this candidate win its comparison is void.

This vault's own evidence channel already counts friction per session after the fact (`Session friction <id>` records carry `tool_error ×N, retry ×N`), which shows the counting is possible but not that it is available *at completion time*, in the process writing the report. Those are different claims and the second is the one this assumption makes.
