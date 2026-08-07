---
type: Solution
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A patch-shaped merge preserves everything the replace-shaped merge preserved]]

Change what a merge asks for. Instead of the survivor's complete merged body, the caller supplies only what the loser contributes — the sentence or section that says something the survivor does not — and the tool appends it under a dated heading. The survivor's existing prose is never an argument, so it is never at risk from a caller who has not read it.

The mechanics that already work stay: inbound edges repoint, outbound edges union, reserved sections carry across, the loser's file is deleted, git holds what went.

## Why this is the safe shape

The destructive step in the current design is not the deletion — that is recoverable and recorded. It is the silent replacement of the survivor's body by a string the caller may have composed from a title alone. Removing that argument removes the failure mode entirely rather than guarding against it, which is worth more than a guard because it cannot be skipped.

## What it costs

Merged nodes get longer and more seam-y over time: a node merged three times reads as an original plus three appended contributions rather than as one coherent claim. That is a real cost, since the point of merging is to leave one claim where there were two, and a stapled node is arguably still two claims sharing a file. Cleaning that up later needs a genuine rewrite — which needs the body read that the sibling candidate provides.

It also cannot help the instrument-overwrite case at all: `ost_set_instrument` replaces a single field, and there is no patch form of replacing a string.

## How it compares

Strictly safer than "A read that returns one node's body, so a rewrite starts from what is actually there", and strictly narrower — it fixes merging only, and it trades prose quality for safety. If both were built, this would be the everyday path and the body read the one used when a merged node needs tidying.
