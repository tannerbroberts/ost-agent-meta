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

## Definition of done

[[Merge the enabling config into five real project settings files and check nothing was lost]]

```
npx vitest run test/config/settings-merge-safety.test.ts
```

Green means five real settings fixtures — including one that already enables other plugins and one carrying comments and unusual formatting — keep every setting they started with after the merge, and at least four still parse without hand-fixing. It is red today because no merge routine exists.

**Safety is the whole value here, not a precondition of it.** This candidate's advantage over its siblings is that it removes the failure rather than detecting it, and that advantage survives only if the write is safe. If merging is unsafe, this is not a setup-time fix at all — it is a way to damage an operator's existing configuration at the exact moment they are trying the product for the first time, which is the worst moment available.

**What green does NOT settle.** Five fixtures are not the space of real settings files, and the formats most likely to break a merge are the ones nobody thought to include. It also says nothing about the merge being *correct* — a merge that preserves every existing key and writes an enabling block that does not actually enable anything passes this command cleanly.
