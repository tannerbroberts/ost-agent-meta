---
type: Assumption
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[One normaliser collapses the read-before-write family and keeps three permission denials apart]]

**Kind: feasibility.**

**The belief, stated so it could be false.** Grouping assumes there is a normalisation that collapses the same refusal across sessions without collapsing different refusals into each other. The corpus makes that non-obvious in both directions. `Claude requested permissions to use mcp__ost-agent__ost_debt` and `…ost_check` and `…ost_read_repo` differ only in a tool name — strip identifiers too eagerly and three distinct withheld capabilities become one entry, and the tree loses the fact that three separate grants are missing. Keep identifiers and the paths and session ids in `File has not been read yet` variants keep 76 items at 76.

**What would make it false.** No normalisation exists that both collapses the read-before-write family across sessions and keeps the three permission refusals distinct.
