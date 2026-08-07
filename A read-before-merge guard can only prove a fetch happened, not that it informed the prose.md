---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Satisfy the guard with a bare fetch that discards the body, and require the merge to go through]]

This guard is worth building only if satisfying it is meaningfully harder than ignoring it. The mechanism available is a session-scoped record that the survivor's body was fetched — which is what the file tools' read-before-write check does.

The belief that could be false is that this is enough. A caller under pressure can issue the fetch, discard the result, and compose from the title exactly as before; the guard is satisfied and the hazard is untouched. If that is how it plays out, the guard buys nothing but a wasted call per merge, and this vault's own friction corpus shows read-before-write refusals are already among its most frequent recorded costs.

Stating it this way makes it falsifiable in the useful direction: the test should try to defeat the guard, not confirm it. A guard that cannot be trivially satisfied by a bare fetch would be evidence the assumption is false and the solution stronger than claimed.

## What a passing test here would NOT settle

Nothing about whether real callers actually take the shortcut — only that the shortcut exists. Whether it gets used is behavioural and would need observation of real passes, not a spec.
