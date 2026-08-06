---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Give the skill's existing instruction a mechanism. The skill already tells the agent "if an item reveals no genuine need, skip it" — but there is no way to record a skip, so a skipped item is indistinguishable from an unread one and comes back next pass. A dismissal action takes the evidence id and a written reason, marks the record read-and-skipped, and removes it from `unmappedEvidence` without creating a node.

**Why this one.** It closes a gap between what the agent is told to do and what it can do. That gap is currently paid for every pass: this pass read four records in full, judged all four redundant, and had no way to say so — so the next pass will read them again and reach the same conclusion at the same cost. A written reason on the record is also the only artefact any of these three candidates produces that a human can audit later to see whether the skipping was honest.

**How it compares to its siblings.**
- Both siblings keep the signal. This one deliberately discards it, which makes it the weakest answer for the recurring frictions and the only workable answer for records that genuinely reveal nothing — a session whose sole friction was a typo, say.
- It is also the only one that works on the records already in the queue with no migration: clustering changes future emissions, corroboration needs a new edge type, and this needs one flag and a reason string.
- Sequenced honestly, this is the release valve and not the fix. If it ships alone, the likely outcome is a pass that dismisses in bulk to reach `done`, and the operator's self-observation channel quietly becomes a no-op that reports success.

**Where this fails, stated so it can be judged rather than assumed.** It creates a way to make work disappear by asserting it was worthless, on a surface whose whole design premise is that the agent cannot clear its own gates. The reason string is the only check, and it is written by the party doing the dismissing. That is a real objection and it is why this is third of three: the same argument the tree makes against an agent marking its own solutions validated applies here almost unchanged, and the tree already carries a bucket for it ("The agent narrows its own capability to get past a gate I set").

**Cost.** The smallest change of the three — a flag, a reason, and a filter — and the largest change to what the agent is permitted to decide, which is the wrong ratio and worth saying out loud.

⚠️ Unvalidated. Proposed by an unattended agent for its own convenience; a human should weigh whether the drain is worth the permission it grants.
