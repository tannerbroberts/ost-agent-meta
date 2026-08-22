---
type: Solution
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The build loop keeps no memory across firings of which targets already failed their own instrument]]

Instead of depending on the vault's `deferred` status being set (which requires a human, or a maintenance pass, to notice the build report and act on it), have the build loop itself record — in its own state, not the tree's — that it tried a target and the target's own instrument was still red after the build. On its next run, skip anything in that ledger unless the underlying node file has changed since the ledger entry was written.

**Why this is a genuinely different mechanism from the other two.** Both siblings fix how the loop reads the *tree's* status field. This one does not touch the tree at all — it makes the loop self-limiting the first time it fails a target, before any human or maintenance pass has had a chance to defer it. It would have prevented the second re-selection (2026-08-16) even before the first build report was read by anyone.

**What would make this the wrong pick.** It duplicates state the tree is supposed to hold as the single source of truth (per this vault's own append-only, git-tracked design), and a loop-side ledger that drifts from the vault's own status is a second place the same fact can go stale. It also does nothing for the actual observed bug if the root cause turns out to be the status-check being absent or stale (the other two solutions' failure modes) rather than the loop simply lacking any memory of past attempts.

⚠️ Unvalidated. Proposed by an unattended pass; the three build reports don't distinguish which of the three mechanisms (or some other cause) is actually responsible, so all three are recorded as a real consideration set rather than one being picked as the fix.

## Definition of done (added 2026-08-22 unattended sweep, repo sight held)

"A target whose instrument stayed red after a build is skipped by the next firing"

```
npx vitest run test/loop/build-attempt-ledger.test.ts
```

Red today as a no-spec filing, with a bound bar so it is a working permit rather than a vacuous red. Grounded from source rather than guessed: `src/loop/state.ts` establishes `.git/ost-agent/` as the loop's own record directory and names only the health ledger and the firing lock as the files a firing must write, so the ledger this solution proposes has a guaranteed-writable home and does not exist in it yet.

The spec settles feasibility — does the loop skip a target it already failed — and nothing else. Whether a loop-side ledger is the right mechanism, given that it duplicates state the tree is supposed to own, stays a design call for a human.
