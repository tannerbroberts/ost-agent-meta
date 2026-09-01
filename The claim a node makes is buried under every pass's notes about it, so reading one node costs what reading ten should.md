---
type: Opportunity
source: 'USAGE:2026-08-31'
created: '2026-09-01'
evidence: assertion
authorship: machine
---
#Opportunity #compression #needs-customer-interview #unvalidated #evidence/assertion
[[Stop writing the visit log — a pass with nothing decision-changing to say appends nothing]]
[[Split every node into a claim file and a commentary file, and return the claim by default]]
[[Hand the oversized body to the harness's own compaction and store nothing new]]

**The need (reader's voice):** "I opened the node to find out what it claims. The claim was in the first paragraph. The other twenty-nine thousand characters were eight passes telling me they had looked at it. I only had budget to open three nodes, and this was one of them."

**Why this is a need and not a style complaint.** A node's cost to read is paid by every future reader, and it grows monotonically because appending is the cheapest write on the surface and consolidating is the most expensive. The finding a node protects stays the same size while the record of visits to it does not, so the ratio of claim to commentary decays with every pass. Past some point the node is still correct and no longer readable, which is the same thing as not being there — and worse, because it consumed the budget that would have read the nodes that are.

**First-party measurements taken this pass.**

- *The trace.* `USAGE:2026-08-31` is a mechanical rollup of 527 tool invocations across 21 sessions, with no narrator. Writes were 55 of 527 (10.4%). Within those writes, appends onto existing nodes (22) outnumbered new nodes (11) two to one, with 7 edits and 1 status change. So the dominant write this product performs on itself is growing a node that already exists.
- *What that costs a reader, measured directly.* This pass opened three Solution bodies from the instrument bucket. One was 30,395 characters, of which roughly the first 2,300 carry the candidate's actual argument and the remainder is eight dated sections appended by earlier passes. The second was 8,875 characters with the same shape. Reading those two consumed more of this firing's window than the entire sweep response that named 517 outstanding items.
- *The tree already fights this per-node, which is the tell.* At least two nodes carry hand-written local conventions invented to hold their own growth down — one Issues bullet recording that seven near-identical annotations were consolidated into one standing finding, another node's sections each opening "Kept short, per this node's own convention." Each node is separately inventing the same rule. A defect that every node has to solve locally is one the surface has not solved.

**Litmus test (more than one way to address this?):** Yes, and they are not variants of each other — a size budget past which a node refuses further appends until it is consolidated; a separate commentary file per node so the claim stays short and the visit log lives elsewhere; a write-time rule that a pass may only append what changes a decision, rather than what records a visit; automatic consolidation triggered when N dated sections accumulate; a read-time rendering that returns claim-first with the commentary collapsed behind a flag. Passes.

**How this differs from the siblings beside it.** "I only find out an artifact is too big to read after the read has already cost me the turn" is about learning the size before paying it — it takes the size as given and asks for a probe. This node is about why the size got that way and whether it had to. "The tree never revisits itself, so old nodes rot and tried things get tried again" is about staleness: a node whose content has gone out of date. A node can be perfectly current and still unreadable, and the repair for one does nothing for the other. Torres's test: a per-node append budget serves this node and neither sibling; a staleness decay serves that sibling and does nothing to this one.

**Provenance and limits, stated so this is not over-read.** The call counts are machine-recorded and are one day of one operator's usage — 2026-08-31 only, not a trend. The character counts are three node bodies chosen because the sweep named them, not sampled at random, so nothing here is a distribution over the tree's 1,596 nodes. The claim that the appended material is mostly restatement is this reader's judgement of two bodies, not a measurement anyone could repeat mechanically; a census over node sizes and section counts would settle it cheaply and has not been run. And the whole thing grounds usability of this product by its own agent — it is not evidence that any outside person wants anything, and it stays at the assertion floor for that reason.

**For a human to review:** whether the repair belongs at the write boundary (refuse the append) or the read boundary (return the claim, hide the log) is a real fork, and the two have opposite failure modes — the first loses findings nobody consolidated, the second keeps paying to store what nobody reads.

Unvalidated. Distilled by an unattended sweep 2026-08-31; a human to review.

## The census this node calls open, run whole-tree (2026-08-31)

Kept short deliberately: a long section here would refute its own subject.

**The open item.** This node's limits paragraph says the claim that appended material is mostly restatement "is this reader's judgement of two bodies, not a measurement anyone could repeat mechanically; a census over node sizes and section counts would settle it cheaply and has not been run." Run now, with a read-only Grep over every Markdown file in the vault.

**Operational definition.** A visit-log section is a `## ` heading carrying a four-digit year — which catches both forms this vault uses, the leading `## 2026-08-31 — …` and the trailing `… (2026-08-30)`.

**The counts, whole-tree rather than a sample.** 307 such sections across 141 node files, against 1,606 nodes. Six further matches fall in `.ost-agent/` evidence and inbox files and are excluded from both figures.

**The finding is concentration, and it was not predictable from the two bodies this node was built on.** 13 nodes carry five or more dated sections, and between them hold 97 of the 307 — 32% of all visit-log commentary sitting on 0.8% of the tree. Roughly 91% of nodes carry none at all. The heaviest is "My unattended runs recover from tool errors and retries I never find out about" at 16 sections, and the second "A pass that cannot see the repository cannot set an instrument at all" at 13. Neither has figured in this node's argument, which was built from the 30,395- and 8,875-character bodies that happened to surface in the instrument bucket.

**Size against section count, from nine bodies read in full this pass.** Nodes carrying no dated section measured 2,309, 2,816 and 4,614 characters; one dated section, 4,948, 7,479 and 8,875; two, 9,264; nine, 30,395 and 47,490. The claim itself stays roughly 2–5KB across the whole range. What scales is the log, which is this node's thesis stated as a measurement rather than as a reading.

**What this does to the fork this node hands a human.** A write-boundary rule — refuse the append past a budget — would be inert on 91% of the tree and would bite precisely the 13. That is an argument for it rather than against: a rule that fires rarely and lands accurately is cheap to live with. A read-boundary rule — return the claim, collapse the log — must be paid on every read of every node in order to help those 13. So the concentration favours the write boundary. It does not settle the other half of the fork, which is whether refusing an append loses findings nobody goes back to consolidate.

**Limits, stated so this is not over-read.** Section count is a proxy for commentary volume and counts only headings carrying a year, so a visit-log section headed without one is missed and 307 is a floor rather than an exact figure. The nine sizes are nodes this pass happened to open for other reasons, not a random sample, so the size-to-sections relationship is an illustration and not a fitted curve. And nothing here measures whether any individual section's content is restatement — that judgement is still unmade, and the concentration result does not depend on it.

_Method: read-only Grep over this vault's own Markdown, plus `ost_read_tree` bodies for the nine sizes. Observed structure of this product's vault; grounds usability, not desirability. No test was run, no rung moved, no instrument set, no status changed, and no node was created._
