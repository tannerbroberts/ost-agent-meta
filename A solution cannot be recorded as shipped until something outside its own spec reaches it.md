---
type: Solution
source: >-
  INBOX:friction/2026-08-10-friction-pr-80-shipped-a-pass-claims-the-work-item-before.md
created: '2026-08-10'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The idea.** Move the check from the repository to the tree. `status: shipped` stops being a sentence a pass can write about a solution and becomes a claim with a required witness: the node must name a path — a script line, a registered command, a call site — by which the built thing is reached in ordinary operation, and the reader of that field checks the path resolves. A solution whose mechanism exists but is unreached is `unvalidated` with a stated reason, not shipped.

**Why here rather than in the code.** The two siblings both audit the repository, and the repository is not where the false statement lives. Nobody reads `src/loop/claim.ts` and concludes the problem is solved; they read a tree node saying shipped, or a changelog line, or a rollup that counts it as built. The rollup pasted at the head of every pass reports "built 18% (8/45 runnable)" per bucket, and every one of those numerators is a status field. If a status can be true of a module nothing calls, the built column is measuring the existence of files.

**Contrast with siblings.** The census measures the problem; the CLI rule fixes one class of it at the source; this one changes what the tree is allowed to assert regardless of which classes the other two cover. It is also the only one of the three that touches the numbers a human actually reads.

**Where it fails, and it is a real cost.** This makes `shipped` harder to earn at exactly the moment the tree is already accused of never saying done. Five solutions in the current `solutionsMissingInstruments` bucket carry `shipped` and would each need a witness path added or be demoted — and demoting five real, working mechanisms to satisfy a bookkeeping rule would be a worse tree, not a better one. Whether the field should be retrofitted or only required going forward is a decision this node does not make.

The deeper risk: a witness path is prose the same pass can write, so this hardens a claim by asking for a second claim from the same author. It is only worth anything if something resolves the path mechanically, which is the sibling census wearing a different hat.

**Cost.** Medium — a frontmatter field, a reader, a migration decision for existing shipped nodes.

⚠️ Unvalidated. Agent-ideated.
