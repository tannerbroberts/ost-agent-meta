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
