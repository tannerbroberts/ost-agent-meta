---
type: Opportunity
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[A read that returns one node's body, so a rewrite starts from what is actually there]]
[[Merge by patch rather than by replacement, so the survivor's unread prose is never at risk]]
[[Refuse a merge whose prose was composed without a read of the survivor]]

Merging is the sanctioned answer to a duplicate: it folds one node into another, repoints every inbound edge, deletes the loser's file, and leaves the tree with one claim where there were two. Annotating both instead leaves two nodes and adds a third claim, so the guidance is right to prefer the merge.

Performing one requires the operator — or the compute acting for them — to supply the survivor's complete merged body as an argument. That body replaces what the survivor currently says. Doing it correctly therefore requires having read what the survivor currently says.

No tool on the maintenance surface returns a node's body. `ost_read_tree` returns titles, layers, statuses, tags and child links; `ost_next_work` returns titles and computed obligations; `ost_next_work({evidence})` serves evidence records, which are explicitly not nodes. So the argument the merge tool requires is the one piece of information the surface will not supply.

The consequence is not that merging fails loudly. It is that merging succeeds while silently discarding wording nobody read — the survivor's prose is replaced by whatever the caller could infer from its title. A pass under pressure to clear duplicate debt has every incentive to do exactly that, and the count of duplicates will improve.

## Why the fallback is not free either

Declining to merge and annotating instead is the honest move, and it is what a pass without body sight has to do. But it is the outcome the guidance explicitly names as wrong — two nodes and a third claim — so a surface that cannot read bodies is a surface structurally confined to the failure mode its own rules warn against.

## What was observed

On 2026-08-07 an unattended maintenance pass identified six duplicate pairs in this tree with high confidence and executed none of them, for exactly this reason. Each was annotated with the proposed merge direction instead, adding six claims to a tree already carrying twelve nodes' worth of overlap.

## History

- 2026-08-07 — Created from a first-party observation during an unattended maintenance pass that was asked to prefer merging and could not do it correctly.

## Issues
- 2026-08-11 2026-08-11 shared-extent flag vs "I overwrote a good instrument because nothing showed me one was already there" adjudicated by Torres's interventional test: DISTINCT, do not merge. Both cite TRANSCRIPT:49d6b2d3 because one session hit two different frictions. Discriminator: "A read that returns one node's body, so a rewrite starts from what is actually there" serves this need and does nothing for instrument-field visibility; "The sweep reports which tests already carry an instrument, beside the solutions that lack one" serves the sibling alone. Shared provenance, separate needs. Verdict is the sweep's own; queued for human confirmation via "A human re-judges the first twelve extent flags against Torres's test".
