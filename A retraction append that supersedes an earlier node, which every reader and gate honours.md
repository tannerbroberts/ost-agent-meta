---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Audit every consumer of the tree for whether it would honour a retraction flag]]

Nothing is deleted; a later append declares an earlier node retracted, names the reason, and every consumer of the tree — the sweep, the gates, the duplicate scan, the counts — reads that declaration and excludes the node. The history stays complete and legible, and the live tree stops carrying the mistake.

The vault already does a version of this: a `deferred` node is withheld from the duplicate scan while still counting toward every gate. Retraction is that mechanism made explicit and made total, so a node can be taken fully out of circulation without anything being lost.

**Compared to the alternatives.** This is the only option that helps after the fact, which makes it the only real answer to the need as stated — preview and a wider refusal set both act before the write and do nothing for what is already on disk. The price is that every reader must be taught to honour retraction, and a reader that forgets is worse than no retraction at all, because the node now looks handled while still being counted.

**What would make this the wrong pick.** If retraction is cheap to invoke, it becomes an undo button, and append-only stops meaning anything in practice. Who may retract, and on what grounds, is the design question — and it probably belongs to a human, not to the pass that made the write.

## Definition of done

[[Audit every consumer of the tree for whether it would honour a retraction flag]]

```
npx vitest run test/ost/retraction-consumers.test.ts
```

Red today: retraction does not exist, so no consumer can honour it. Green when one planted retracted node is excluded by every node-reading path — check, debt, the status rollup, the duplicate scan, the sweep, and each gate.

**What a green spec does not settle.** It fixes the consumer set as of today. The test node names the real long-term risk itself: a reader written next year will not know retraction exists unless something enforces it, and a passing spec over today's consumers says nothing about that.
