---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A dismissal can be made auditable enough that a human can catch a dishonest one]]

**The idea.** Give the skill's existing instruction a mechanism. The skill already tells the agent "if an item reveals no genuine need, skip it" — but there is no way to record a skip, so a skipped item is indistinguishable from an unread one and comes back next pass. A dismissal action takes the evidence id and a written reason, marks the record read-and-skipped, and removes it from `unmappedEvidence` without creating a node.

**Why this one.** It closes a gap between what the agent is told to do and what it can do. That gap is currently paid for every pass: this pass read four records in full, judged all four redundant, and had no way to say so — so the next pass will read them again and reach the same conclusion at the same cost. A written reason on the record is also the only artefact any of these three candidates produces that a human can audit later to see whether the skipping was honest.

**How it compares to its siblings.**
- Both siblings keep the signal. This one deliberately discards it, which makes it the weakest answer for the recurring frictions and the only workable answer for records that genuinely reveal nothing — a session whose sole friction was a typo, say.
- It is also the only one that works on the records already in the queue with no migration: clustering changes future emissions, corroboration needs a new edge type, and this needs one flag and a reason string.
- Sequenced honestly, this is the release valve and not the fix. If it ships alone, the likely outcome is a pass that dismisses in bulk to reach `done`, and the operator's self-observation channel quietly becomes a no-op that reports success.

**Where this fails, stated so it can be judged rather than assumed.** It creates a way to make work disappear by asserting it was worthless, on a surface whose whole design premise is that the agent cannot clear its own gates. The reason string is the only check, and it is written by the party doing the dismissing. That is a real objection and it is why this is third of three: the same argument the tree makes against an agent marking its own solutions validated applies here almost unchanged, and the tree already carries a bucket for it ("The agent narrows its own capability to get past a gate I set").

**Cost.** The smallest change of the three — a flag, a reason, and a filter — and the largest change to what the agent is permitted to decide, which is the wrong ratio and worth saying out loud.

⚠️ Unvalidated. Proposed by an unattended agent for its own convenience; a human should weigh whether the drain is worth the permission it grants.

## Definition of done

"Dismiss ten records and require every one to be attributable and reversible"

```
npx vitest run test/ost/evidence-dismissal-audit-trail.test.ts
```

Red today: there is no dismissal action, so every assertion fails against an absent mechanism.

Do not read a green run as clearance to ship this. It proves the log is honest; it does not prove anyone reads it, and the parent assumption turns entirely on that. Of the three candidates under this opportunity, this is the one that grants an unattended agent new authority, and a human should choose it deliberately or not at all.

The test title is quoted rather than linked because it is already wikilinked once by its parent Assumption, and a second link would fail `check`'s single-backlink rule.

## Issues
- 2026-08-22 2026-08-22 (unattended sweep, repo sight held) — THIS APPEARS TO BE BUILT, and the node still reads as an unvalidated candidate. `src/knowledge/dispositions.ts` implements an append-only JSONL disposition ledger at `.ost-agent/dispositions/dispositions.jsonl`; a `closed` entry takes its subject off every work bucket via one shared predicate (`isDisposed`), and `omitDisposed` discloses each withheld item on the response that withheld it. The write is the CLI command `ost-agent dispose` (`test/cli/dispose.test.ts`), deliberately kept off the agent surface — the module calls it "the highest-risk write on the surface" because a pass that could dismiss its own work list has a meaningless completion signal. `test/evidence/corroborate-disposition.test.ts` pins the behaviour end to end: thirty ids filed, thirty cleared from `unmappedEvidence`, no node created, node file byte-identical so no rung moved. Status NOT changed by this pass: marking a solution `shipped` changes how `verifyInstrument` treats a first-run green (`trustsShippedStatus`), which is a gate effect, and this pass read source without executing anything. A human should confirm and promote. Parent context recorded on "Every session leaves an evidence record that restates a need the tree already holds".
