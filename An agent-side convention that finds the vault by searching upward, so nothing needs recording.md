---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Put two vaults on one machine and see whether the upward search picks the right one]]

No file records the link. Instead every tool that wants the vault looks for it the same way version control finds its own root: search the current directory and then upward for a directory with the vault's recognisable shape, and use the first one found. The connection is derived at the moment it is needed rather than stored.

Because nothing is written down, nothing can be wrong. A vault that moves is found in its new place; a project that is cloned finds whatever vault sits above the clone.

**Compared to the alternatives.** Uniquely immune to going stale, which is the failure a pointer file has and cannot avoid. It also requires every consumer to implement the same search and agree on what a vault looks like, and it silently binds a project to whatever vault happens to sit above it — which on a machine with several vaults is a mistake that produces no error at all, only the wrong tree.

**What would make this the wrong pick.** Discovery by convention works well when there is exactly one plausible answer and badly when there are two. It also cannot express intent: a project that deliberately has no vault is indistinguishable from one whose vault has not been found yet.
