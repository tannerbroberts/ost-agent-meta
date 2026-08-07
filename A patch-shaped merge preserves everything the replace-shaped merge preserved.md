---
type: Assumption
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Changing what a merge asks for must not change what it guarantees. The current merge repoints every inbound edge at the survivor, unions the loser's outbound edges in, carries the loser's reserved sections across so no recorded result is lost with the file, and refuses the one case that would clear a gate nobody earned — folding a node carrying a result into one that has none.

All of that is independent of how the survivor's prose is supplied, so the patch form should keep it exactly. The assumption is that it does, rather than that some part of the mechanics is entangled with rewriting the body — which is plausible, because a tool that rebuilds a file from a supplied body may be reconstructing edges from that body's wikilinks rather than from a separate index.

Feasibility, and settled by code rather than by anyone's afternoon.

## What a passing test here would NOT settle

Whether stapled prose stays readable after several merges, whether callers can identify what the loser uniquely contributed, or whether operators prefer this shape. Only that the patch form loses nothing structural.
