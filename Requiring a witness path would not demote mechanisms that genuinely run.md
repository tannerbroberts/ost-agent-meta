---
type: Assumption
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[Resolve a witness path for every node the tree already calls shipped and count the failures]]

**The belief, stated so it can be false.** The solutions this tree already calls `shipped` can each name a reachable witness path, so adding the requirement documents what is true rather than demoting working mechanisms into `unvalidated`.

It is false in the obvious way: some shipped nodes describe behaviour that is real but diffuse — a refusal inside a write boundary, a redaction inside a funnel — and there is no single line anywhere that "reaches" it in the sense a path resolver could check. If a third of the shipped nodes cannot produce a witness, the rule does not tighten the tree, it corrupts a status field that was accurate.

**Category:** feasibility.

**Why it is the riskiest belief here and not the demand question.** Whether operators want a stricter `shipped` is a preference; whether the existing corpus can satisfy it is a fact about nodes that already exist, checkable today, and it decides whether the solution is buildable at all. If the answer is no, the honest version of this solution is "required going forward, existing nodes grandfathered", which is a materially different thing to build and worth knowing before anyone starts.
