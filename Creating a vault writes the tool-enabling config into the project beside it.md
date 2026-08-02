---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Merge the enabling config into five real project settings files and check nothing was lost]]

Setup writes the enabling configuration at the moment the vault is created, into the project directory the vault lives in, so that having a vault and having the tools that operate on it become the same event. The step that is currently invisible and manual stops existing rather than becoming better documented.

**Compared with the alternatives:** this is the only candidate that removes the failure instead of detecting it, and it costs nothing at run time. Its weakness is reach — it fixes vaults created after the change and does nothing for the ones already on disk, which is exactly the case that produced four toolless passes. It also writes into a file the operator may own and have opinions about, so it must merge rather than overwrite, and merging someone else's configuration is where this gets harder than it looks.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.
