---
type: Solution
status: unvalidated
source: 'agent:P3_ideate'
created: '2026-07-24'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Reading the whole tree at once yields reorganisations a human accepts]]
[[A whole-tree read stays coherent as the tree grows]]

Periodically read the entire tree at once and propose how it should be reorganised — merge duplicates, split overloaded opportunities, re-parent nodes whose real home has become clear, retire branches evidence has moved past. Proposals only; a human confirms structural change.

**How it differs from its siblings:** compression in the founder's sense — the map gets *smaller and truer* as it grows, rather than only longer. The siblings manage individual nodes' freshness and history; this one changes shape.

**Trade-off:** expensive in context and compute, and re-organisation is where an agent can silently destroy meaning; append-only proposal is the safeguard.

**Riskiest assumptions to test:** that a whole-tree read stays coherent as the tree grows (feasibility); that restructuring proposals are ones a human accepts (desirability); that a reorganised map measurably beats an accreted one (desirability).

Status: agent-originated candidate. Unvalidated.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "One re-synthesis pass with human accept-reject" — moved under "Reading the whole tree at once yields reorganisations a human accepts" — the belief this test measures now has a node of its own

## Definition of done

"Run re-synthesis against a vault larger than every cap and require it to see every node"

```
npx vitest run test/ost/whole-tree-read-scale.test.ts
```

**This covers the feasibility half only.** This node's body names three riskiest assumptions and only one of them had a test: the desirability claim that restructuring proposals are ones a human accepts. The feasibility claim it names first — "that a whole-tree read stays coherent as the tree grows" — had no node until this pass, so the cheaper and more likely failure was the untested one. It now has a node and a command.

The command settles whether the re-synthesis input is the whole tree or a capped sample presented as one. It does not settle whether a human accepts the proposals, and it does not settle the third assumption this node lists, that a reorganised map measurably beats an accreted one. Both of those name a person as the measurement.

**Why this is a live risk rather than a precaution.** This vault holds 1158 nodes, and every whole-tree channel an agent has is already capped — `ost_read_tree` truncates and reports `shown`/`hidden`, and `ost_next_work` caps every list at 25. A re-synthesis run built on those channels today would be proposing merges and retirements over the visible fraction while reporting a whole-tree pass. The assumption node records the observation in full.

The red is a `no-spec` red and the test node says so; the assertions the spec must make are written out there, so a builder inherits a designed test rather than a blank file.
