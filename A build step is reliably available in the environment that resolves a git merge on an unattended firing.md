---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A merge driver invoked without the build toolchain fails loudly instead of writing a half-built dist]]

Feasibility belief: the process performing the merge (which may be a lighter-weight or more sandboxed context than a full firing) actually has the toolchain and permissions to run the project's build when the merge driver invokes it — if not, the driver itself becomes a new failure point.
