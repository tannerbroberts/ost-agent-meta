---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A run's boundaries and work are recoverable from the commits alone]]

Every mutation already auto-commits with a message naming the tool and its subject. Read the history instead of asking the run: the commits between the run's first and last are exactly what it accomplished, in order, and they exist whether or not the run survived to say anything about itself.

This has a property no self-report can have. A run that lied, crashed mid-sentence, or was killed before it could summarise still cannot alter what is in the log, because the log was written by the writes themselves rather than by the narrator.

**Compared to the alternatives.** Needs almost nothing built — the data is already there, and what is missing is a way to bound a run within it. That bound is also the weakness: distinguishing one run's commits from a concurrent run's, or from a human's, is not obviously solvable from git alone, and the tree already has an open question about whether a pass can tell a human edit from its own. Against a forward-written journal, this is more trustworthy and less expressive: it sees writes and is blind to everything a run did that wrote nothing.

**What would make this the wrong pick.** Much of what a run does is reading, deciding, and declining to act. A history-derived account will show a run that spent an hour correctly concluding nothing needed doing as a run that did nothing at all.

## History
- 2026-08-05 unlinked [[Try to bound five past runs within the commit history without being told where they started]] — moved under [[A run's boundaries and work are recoverable from the commits alone]] — the belief this test measures now has a node of its own

## Proving this

[[Try to bound five past runs within the commit history without being told where they started]]

```
npx vitest run test/loop/run-boundary-from-history.test.ts
```

Red today: nothing in the repository derives a run's boundaries from the commit log, which is the one thing this solution says is missing. Green when the bounding exists and can exclude a concurrent run's or a human's commits from the span.

**What a green run would not settle.** It proves the boundaries are recoverable, not that the account they produce is worth reading. This solution's own stated weakness — that a run which spent an hour correctly concluding nothing needed doing appears as a run that did nothing — is a desirability question about the output, and no exit code touches it.
