---
type: Assumption
created: '2026-08-18'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

Viability belief: sessions that get backgrounded or interrupted almost always have made at least one committed write by that point, so relying purely on git history (with no separate log) doesn't lose visibility into the common case of an interrupted session that did substantial thinking/planning but hadn't yet written anything.
