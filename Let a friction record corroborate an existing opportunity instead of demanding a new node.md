---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Many records from one self-observing actor will not inflate a node's believability]]

**The idea.** An evidence record can be attached to an opportunity that already exists, as an additional source, without creating anything. The record leaves `unmappedEvidence`; the opportunity's source count goes up by one; nothing new is written to the tree but a line in the opportunity's History.

**Why this one.** It is the only candidate that turns the volume into something valuable. The rollup already reports "N source(s)" per bucket and a believability floor per subtree, so the machinery for counting independent sources exists and is displayed — it is just that the only way to feed it is to create a node. The fourth recurrence of a friction ought to make its opportunity harder to argue with. Today the fourth recurrence makes a fourth node, which makes the opportunity *easier* to argue with, because the evidence is spread across duplicates that each look thin.

**How it compares to its siblings.**
- "Cluster friction records by signature before the queue sees them" reduces the count upstream and is cheaper, but a cluster is still an unmapped item demanding a node, and clustering discards which sessions contributed — the thing that makes recurrence persuasive.
- "Record a read-and-skipped judgement with a reason" also drains the queue, and explicitly throws the signal away. That is the right answer for genuinely irrelevant records and the wrong one for the recurring frictions, which are most of them.
- This one is the only one where a busy month of sessions leaves the tree *more* believable rather than merely no bigger.

**Where this fails, stated so it can be judged rather than assumed.** It hands the agent a cheap way to make a node look well-sourced: attaching thirty of its own transcripts to one opportunity produces "30 sources" that are all the same actor observing itself, which is not thirty independent voices and must not read as one. The believability ladder's actor-based ceiling is the existing defence, and this solution leans on it much harder than anything does today. It also needs a judgement — does this record corroborate that opportunity? — made 65 times, by the same agent whose attention the queue was consuming in the first place, so the saving is smaller than it looks.

**Cost.** A new edge type from evidence to opportunity, a change to how `unmappedEvidence` is computed, and a source-count display that distinguishes actors. Middling.

⚠️ Unvalidated. Proposed by the agent that generated all 65 records, which is the party that benefits most from them counting for something.

## Definition of done

"Attach thirty self-observations to one node and require the rung not to move"

```
npx vitest run test/adapters/corroboration-actor-ceiling.test.ts
```

Red today: there is no way to attach an evidence record to an existing node, so the spec fails on its first line against a missing mechanism — and the actor-count assertions fail independently, because the rollup prints a bare "N source(s)" with no actor breakdown.

The test title is quoted rather than linked because it is already wikilinked once by its parent Assumption, and a second link would fail `check`'s single-backlink rule.

## Issues
- 2026-08-22 2026-08-22 (unattended sweep, repo sight held) — THIS APPEARS TO BE BUILT, essentially as specified. `src/knowledge/dispositions.ts` carries a typed verdict vocabulary `corroborates` / `no-genuine-need`, and a `corroborates` entry is REQUIRED to name the node the item was counted toward (`appendDisposition` throws without it) — the pointer this candidate argued for. `corroborationsFor(ledger, node)` reads back every live acknowledgement counted toward a node. The design explicitly protects the failure this candidate risked: `test/evidence/corroborate-disposition.test.ts` files thirty transcript ids against one opportunity and asserts the node's `evidence:` rung and the rollup's `corroborators` count are UNCHANGED — because `corroborators` counts distinct node `source:` values and a ledger filing never writes one. So thirty recordings of one channel stay one channel observed thirty times, rather than inflating into thirty voices. Reached via the human CLI `ost-agent dispose --verdict corroborates --node "<title>"`, not from any agent surface. Status NOT changed by this pass (gate effect via `trustsShippedStatus`; nothing was executed). A human should confirm and promote.
