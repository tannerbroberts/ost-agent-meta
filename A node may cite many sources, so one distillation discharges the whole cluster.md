---
type: Solution
source: 'TRANSCRIPT:3b9eaea5-d098-4f47-ad0a-65871012d639'
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Every reader of source can take a list without breaking the nodes that carry a string]]

**The idea.** Make `source` a list. A node distilled from forty session-friction records cites forty ids, and the mapped-ness derivation — *"evidence is mapped iff some node cites its id as that node's source"* — is unchanged except that "cites" now reads a list. One distillation, forty records discharged, and the tree gains one node instead of forty.

**Why this is a small change and not a schema upheaval.** The relation in `src/processes/tree.ts` is already derived rather than stored, deliberately, and the derivation is a lookup over node frontmatter. A single string is a list of one. Everything downstream that reads `source` for provenance — the believability ladder's `classifyProvenance`, the near-miss check that catches `inbox:note.md` typed against `INBOX:note.md` — reads one value today and would read each in turn.

**What it improves beyond the count.** Corroboration becomes visible. Forty records saying one thing is a stronger observation than one record saying it, and today the tree has no way to write that down: thirty-nine of them get dismissed or ignored, and the node that survives cites a single session as though it were the only instance. The rollup's `sources` column would start meaning what a reader assumes it means.

**Contrast with siblings.** This treats the cluster as worth distilling; "One human dismissal can name a class" treats it as worth hiding. They are not variants of each other and could both ship — a class you distil and a class you dismiss are different classes. Against the adapter roll-up, this keeps every raw record on disk and addressable, which matters if a later question needs the individual sessions back.

**Where it fails.** Nothing forces the citation to be honest. A pass under pressure to clear a queue can list forty ids it skimmed, and the tree will show a node resting on forty sources that reads exactly like one resting on forty sources somebody actually distilled. The current one-to-one field makes that lie expensive; this makes it free. Whether a rung ceiling or a spot-check can hold the line is unresolved, and it is the reason this is not obviously the best of the three.

**Cost.** Medium — a frontmatter shape change, every `source` reader updated, and a migration that must leave existing single-string nodes readable.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Cite three ids from one node and require all three to leave the unmapped list"

```
npx vitest run test/ost/multi-source-mapping.test.ts
```

Quoted rather than linked: the test hangs under the Assumption "Every reader of source can take a list without breaking the nodes that carry a string".

Red today as **`no-spec`**. The load-bearing assertion is the rung ceiling: a node citing one `stated` source among two `assertion` sources must cap at `assertion`. That is pre-committed here, before the code exists, because taking the strongest source in a list is both the intuitive implementation and a free promotion.

## Issues
- 2026-08-22 2026-08-22 (unattended sweep, repo sight held) — THE PREMISE LOOKS FALSE FROM SOURCE; consider re-wording before anyone spends time running this. `src/knowledge/dispositions.ts`'s module docstring states the mapping rule outright: "an item is mapped only when a node's frontmatter `source:` equals its id, body citations are invisible to the sweep, and no tool can add a `source:` to an existing node." A node carries ONE `source:` field, so one distillation discharges exactly one evidence id — a cluster cannot be discharged by citing many ids in a body, because the sweep never reads the body. Not recorded as a result: this pass read source and executed nothing, and recording a result is a human's `ost-agent result`. What the finding does suggest is that the real answer to the cluster problem is the disposition ledger (`ost-agent dispose`), which discharges any number of ids without touching a node at all — see the 2026-08-22 entry on "Every session leaves an evidence record that restates a need the tree already holds".
