---
type: Solution
status: unvalidated
source: 'agent-ideation — from the Obsidian rename incident in this vault, 2026-07-24'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Rename-shaped link breaks are common enough in the histories to be worth detecting]]

**The idea.** When a node is renamed and the old file is left behind empty, recognize it as a rename rather than as one deletion plus one unrelated creation, and offer to re-point the inbound wikilinks.

**The shape of the evidence.** After the hand-edit in this vault: a 0-byte file at the old title, still referenced by the root Outcome; a new file with a different title carrying the old node's entire body and all 8 of its outgoing links. Same links, same prose, different filename. That is a rename with a very high confidence signal — link-set identity is far stronger evidence than title similarity, and here the titles have almost nothing in common (`Trust an unmonitored agent enough to walk away` → `Any steakholder can start the ost-agent npm package, pour compute and a goal into it, and trust it to efficiently map out the path to accomplishing the goal`), so a naive title-distance heuristic would have missed it entirely.

**Why this ranks below its two siblings, and should be built after them.** Quarantining unknown types is a certain bug with a certain fix. Drift reporting is nearly free and cannot be wrong, because it only ever *tells* the human something. This one requires the agent to *infer intent* and then mutate the tree on the strength of that inference — the one place in this branch where being clever can produce a wrong tree rather than a loud one. If the drift report already surfaces "an empty file is still linked from the Outcome, and a new node appeared carrying the same 8 links," a human resolves it in ten seconds and the automation buys very little.

**Note also that this incident is partly self-inflicted.** Obsidian normally updates inbound `[[wikilinks]]` on rename; here the vault ended up with an empty file at the old path and no link rewrite, which suggests the edit did not go through Obsidian's rename path, or that the two writers raced. Before building rename detection it is worth checking whether the product should simply be a better Obsidian citizen — the cheapest fix to a rename problem is usually not detecting renames.

⚠️ Unvalidated. Proposed by an agent, from a single incident whose cause is not fully established.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Audit both vault histories for rename-shaped link breaks]] — moved under [[Rename-shaped link breaks are common enough in the histories to be worth detecting]] — the belief this test measures now has a node of its own

## Definition of done

[[Audit both vault histories for rename-shaped link breaks]]

```
npx vitest run test/ost/rename-link-repair.test.ts
```

Green means every rename-shaped break in both vault histories is detected from topology alone and the edge repaired. It does not settle the false-positive side, which is where the risk sits: a node genuinely deleted and a node renamed leave similar traces, and repairing an edge to something that was meant to go away is a quieter failure than leaving it broken.
