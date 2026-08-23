---
type: Solution
source: 'INBOX:2026-08-11-observed-build-loop-reports-not-merged-on-merged-prs.md'
created: '2026-08-11'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[What the founder means by highlights is already present in vault history]]
[[Vault history records flip events in a form a mechanical reader can enumerate without a model call]]

A periodic (per-firing or daily) digest that reads what the vault already records — the 20 unsurfaced red-to-green observations existed in history the night the founder said he heard nothing — ranks the entries, and delivers a short highlights message. Nothing new is measured; the gap this closes is that recorded milestones are written where nobody reads.

**Against the alternatives beside it:** batched rather than interruptive, so it trades immediacy for signal density and is harder to tune out. It depends on one belief the flip-announcement does not: that what the founder means by "highlights" is already present in recorded history rather than being a kind of event nothing records yet — his own caveat ("nor am I certain that the highlights are happening as hoped") says he does not know either, which is exactly what a sample digest would settle.

## Definition of done

"A digest built from a fixture vault names every seeded red-to-green flip and nothing else in its top three"

```
npx vitest run test/loop/highlights-digest.test.ts
```

Named in plain text rather than linked, because the test's one backlink belongs to its parent assumption. That assumption — the feasibility half, added 2026-08-23 — is new: until now this candidate rested only on a desirability belief about *what* history holds, with nothing on the tree about whether a mechanical reader can get it back out. Both have to be true for the "nothing new is measured" premise to hold, and only the first was written down.

The command above fails today for the weak reason (no such spec file). The bar it is held to is in the test node and is fixed in advance: all 3 seeded flips named, 0 non-flip entries in the top 3, 0 model calls.
