---
type: Solution
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A read-before-merge guard can only prove a fetch happened, not that it informed the prose]]

Borrow the shape the file tools already use. An editor that refuses to write a file the session has not read is the reason `File has not been read yet` appears throughout this vault's own friction records — it is annoying, it fires constantly, and it stops exactly this class of mistake. Apply it here: the merge tool tracks whether the calling session has read the survivor's body, and refuses when it has not.

The refusal is the product. A pass working a duplicate backlog under pressure will compose from titles if that is permitted and cheap; making it impossible is what changes the behaviour, and the error message is where the caller learns the rule.

## What it depends on

This candidate is not independently buildable — it presupposes a body read exists to satisfy it. On its own it would be a refusal with nothing that can clear it, which would make merging impossible rather than safe. It should be read as a rider on "A read that returns one node's body, so a rewrite starts from what is actually there", not as a rival to it.

## What it costs

The same cost the file tools already pay, visible in this vault's own transcript corpus: read-before-write refusals are among the most frequent friction events recorded here, and they cost a wasted call every time an agent forgets. Adding a fourth surface with that behaviour adds to a tally the operator is already unhappy about — which is tracked separately as its own opportunity, and is a reason to weigh this against the patch-shaped candidate that needs no guard at all.

## How it compares

Against "Merge by patch rather than by replacement, so the survivor's unread prose is never at risk": that removes the hazard, this polices it. Removing beats policing where both are available, so this is the weakest of the three on its own terms — its value is as insurance if the body read is built and merges keep their replace-the-body shape.

## Definition of done

"Satisfy the guard with a bare fetch that discards the body, and require the merge to go through"

npx vitest run test/tools/merge-read-guard-bypass.test.ts
