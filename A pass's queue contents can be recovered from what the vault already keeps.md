---
type: Assumption
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Feasibility. A delta needs a previous state. Either the vault starts storing each pass's queue — a new artefact to maintain — or previous queues can be recomputed from git, since every mutation auto-commits and the tree at any past commit is fully determined. If recomputation works, the delta costs no new storage and cannot drift from the truth; if it does not, this solution carries a whole new record with it.
