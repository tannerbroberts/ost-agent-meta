---
type: Solution
source: 'agent-ideated:2026-08-02-unattended-sweep-priority-order'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Do written reasons get challenged, or only read]]

**The mechanism:** the agent emits one ordered ledger covering every rankable node in the tree, not a single next-build pick, and the write is refused unless every row carries a written reason that cites at least one node title or evidence id. A row whose reason is missing, empty, or citation-free does not get a rank — it lands in an explicitly-named unranked tail, so a gap in the reasoning shows up as a gap in the list rather than as a confident position.

**How it differs from the siblings under the parent.** [[A standing Next Build node the agent rewrites every pass]] names one item, which is the exact thing the founder's statement asked past: an operator cannot plan beyond Monday from a single pick. [[Rank every node by how many blocked tests one build would unblock]] produces a complete order but carries one implicit reason (the count) and cannot express a position that rests on strategy, a governance gate, or cost. This candidate makes the reason the load-bearing artifact and the rank a consequence of it.

**Chief risk, stated plainly:** authored prose is unfalsifiable. An agent can write a fluent justification for very nearly any order, so this mechanism buys legibility without buying correctness, and it is the agent grading its own homework in the sense [[Worry the agent is grading its own homework]] already names. Its defence is that a written reason is at least *challengeable* — an operator can disagree with a sentence in a way they cannot disagree with a silence — but whether reasons actually get challenged is the assumption, not the claim.

**Cost shape:** cheap to build (a refusal at the write boundary plus a rendering), expensive per pass (a reason per row over a 324-node tree, re-authored whenever the order moves).
