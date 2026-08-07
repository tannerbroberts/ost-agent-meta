---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Point the body read at the sidecar and at a node holding results, and require both to be refused or labelled]]

The body read is only safe to add if it can be scoped to nodes and nothing else. The vault already draws this line elsewhere: `ost_read_repo` refuses a vault's own `.ost-agent/` sidecar even when the vault is a configured repo, because evidence bodies are supposed to arrive through one channel with its framing attached.

A new read that takes a title and returns a file could become a second door onto that sidecar, or onto secrets that other tools redact, if it resolves paths rather than node identities. It could also become a way to read reserved sections out of context — `## Results` and `## Instrument Log` are meant to be read by gates, and serving them as ordinary prose invites a caller to treat a recorded result as material it may rewrite.

Feasibility, and answerable from the repository: whether the resolver can be confined to node identities, and whether reserved sections can be returned labelled rather than inline, are both facts about code.

## What a passing test here would NOT settle

That callers given the read will use it before composing merged prose, that the wider read surface is acceptable to an operator storing customer quotes in their vault, or that the read is worth its maintenance. Feasibility answered mechanically leaves desirability, viability and usability where they were.
