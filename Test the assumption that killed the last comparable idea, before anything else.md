---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[What kills solutions in this tree repeats by category, often enough to infer risk from]]

Use the tree's own history instead of anyone's judgement. When a solution comes up for testing, find the solutions most like it that were deferred or abandoned, read what actually killed them, and require a test against that same class of assumption first. Risk is inferred from what has already gone wrong here rather than nominated by whoever is closest to the idea.

This works because failure repeats by category. A vault that has three times abandoned an idea on the same viability question has told you what its riskiest assumptions look like, in its own domain, without anyone having to be objective about it.

**Compared to the alternatives.** The only option grounded in recorded outcomes rather than opinion, and it improves on its own as more ideas die. It needs a history to work at all, so it is useless in a young tree and weakest exactly when the most ideas are alive. It also requires a notion of "comparable", which is the same hard classification problem that appears everywhere else in this tree.

**What would make this the wrong pick.** It looks backward by construction. A genuinely novel solution whose fatal assumption resembles nothing in the history will be gated against the wrong thing and pass, with the gate reporting more confidence than a self-nomination would have.

## Definition of done

[[Check the deferred nodes for whether what killed them repeats by category]]

```
npx vitest run test/ost/deferred-cause-recurrence.test.ts
```

Red today, and worth being precise about why, because this one fails against data rather than against a missing file. Nothing in the repository groups deferral causes — but even once that exists, the assertion still fails: the vault holds one retired node against a required sample of fifteen. The command goes green only when this tree has actually abandoned enough ideas to show a distribution, and the top three causes account for half of them.

**That makes the red itself the current answer.** The node argues this route works from a prior built out of past deaths. A vault with one death has no prior, so the approach cannot help here yet regardless of whether the assumption holds in general. A builder reading this should treat the failing command as a not-yet rather than a defect, and should not build the ordering mechanism until the count clause passes on its own.

**What this does not settle.** Whether failure repeats by category in products at large — the general claim underneath this solution — is untouched by a census of one young vault. And a cause read out of a History line is the cause somebody wrote down, which is not always the cause that operated.

## History
- 2026-08-05 unlinked [[Check the deferred nodes for whether what killed them repeats by category]] — moved under [[What kills solutions in this tree repeats by category, often enough to infer risk from]] — the belief this test measures now has a node of its own
