---
type: Solution
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A body read can serve every node without also exposing the vault's sidecar]]

Add the missing read: a call that takes one node title and returns that node's body, the same way `ost_next_work({evidence})` already serves one evidence record in full. A caller about to merge reads both nodes, composes prose that keeps what each said, and passes it.

This is the direct fix and the smallest one. It changes no existing tool's contract, adds no refusal, and makes the merge instruction followable as written. It also fixes the sibling problems in the same family at once — the same read would show whether a test already carries an instrument, which is the other place this surface writes over what it cannot see.

## What it costs

A body read is the widest new capability of the three candidates here. Every node becomes fetchable in full by anything holding the surface, which matters because bodies are where quoted customer language and reasoning live. It also puts the burden on the caller's discipline: nothing makes a caller actually read before composing, so the failure mode moves from "impossible to do correctly" to "easy to skip", which is a smaller problem but not no problem.

## How it compares

Against "Merge by patch rather than by replacement, so the survivor's unread prose is never at risk": that one removes the need to read at all, which is strictly safer for merging but does nothing for the instrument-overwrite case, and it constrains what a merge can say. This one is more general and less safe.

Against "Refuse a merge whose prose was composed without a read of the survivor": that guard is worthless without this read existing first — there would be nothing to satisfy it with. They compose rather than compete; this is the enabling half.
