---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A key loose enough to recognise a prose verdict is still strict enough to ignore an incidental mention of the same sibling]]

**Mechanism.** Loosen the suppression key for the three extent rules from "an Issues line equal to the issue string" to "an Issues line that names the rule (`shared-extent` / `subset-extent` / `entangled-extent`) and quotes the sibling's title". Every verdict the 2026-08-11, 08-17 and 08-20 passes wrote already has that shape — "2026-08-17 subset-extent flag vs "Nothing kills a candidate…" adjudicated … DISTINCT" — so all of them would have counted on the day they were written. The relation kind is part of the key on purpose: a verdict on a `shared-extent` pairing does not carry over when new evidence turns the same pair into `subset-extent`, which is exactly when a human should look again.

**Variation dimension: automated-vs-manual — fully automated recognition, nothing left manual.** The pass keeps writing verdicts the way it already does; the scanner does the work of recognising them. The disclosure sibling still requires the pass to perform a manual act (quote the key); this one removes that act entirely. What stays deliberately manual is the judgement itself — the scanner never reads whether the verdict said DISTINCT or MERGE, only that a verdict on this rule and this sibling exists, so a pass that wrote "MERGE" and then did not merge has also silenced the flag. That is the cost of this position and it is named here rather than hidden.

**Against its siblings.** Cheaper for the pass than "The extent flag's own text names the annotation that clears it", and retroactive where that one is not; more permissive than "Extent verdicts go through the typed suppression ledger", which would refuse the agent this power altogether.

**Where it fails.** Any prose that happens to name a sibling in quotes next to a rule name — a corroboration note, a cross-reference — reads as a verdict. The assumption beneath is that the key can be loose enough to catch real verdicts and strict enough to miss incidental mentions.

⚠️ Unvalidated. Agent-ideated.
