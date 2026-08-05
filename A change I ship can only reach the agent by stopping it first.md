---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Versioned workflow with scheduled hot-swap and rollback]]
[[Canary the changed process against the old one]]
[[Agent proposes its own workflow changes for one-click adoption]]

The running process holds its policy from when it started. Shipping an improvement means killing the run, and killing the run costs whatever it was in the middle of — so improvements queue up behind a restart nobody wants to spend, and the agent keeps running the version I already know is worse.
