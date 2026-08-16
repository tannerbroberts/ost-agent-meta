---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Give every firing of the build and discovery loops a fresh `git worktree` checked out from `main`, instead of both loops sharing one working directory. A firing's branch, and any edit it makes to the automation scripts on that branch, is confined to its own worktree and is discarded (or merged only through normal review) when the worktree is torn down — there is no shared mutable checkout for policy to leak through between firings. Costs setup/teardown overhead per firing and disk, unlike the cheaper reset-based solution beside it, but also closes the "stuck branch left checked out" drift this opportunity was inferred from, not just the self-modification exploit.
