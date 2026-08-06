---
type: Assumption
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Run the preflight over recorded working-tree states and count the clean sessions it would have refused]]

A preflight that refuses on "the tree is dirty and recently touched" is only useful if that signal separates the dangerous case from the ordinary one. Every working repository has uncommitted changes most of the time, and an operator with a file open in an editor produces the same mtimes as a merge landing.

Feasibility, and the risk that kills this candidate if it is false: if the two are not separable, the preflight either refuses almost always — in which case the run never starts — or is tuned until it refuses almost never, in which case it is decoration. There is no obvious middle setting, and asserting one without measuring it is how a guard ends up switched off by the people it protects.
