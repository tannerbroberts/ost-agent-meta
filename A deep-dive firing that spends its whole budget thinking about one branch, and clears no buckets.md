---
type: Solution
source: 'CONVO:2026-08-11 operator session'
created: '2026-08-11'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Analysis-only firings change decisions rather than producing commentary]]
[[A firing can be given a budget of its own, and its spend can be attributed to the one branch it worked]]

**Mechanism:** a distinct firing type beside the sweep. Input: one branch (the standing `discovery.target`, or a branch the human names for the occasion). Output: sustained analysis appended to that branch's own nodes — sharper framings, newly surfaced assumptions, contradictions between siblings, what the branch's evidence actually supports — and explicitly zero bucket-clearing. The sweep keeps the tree current; the deep-dive is where a hard problem gets an hour of thought instead of a bucket visit.

**Contrast with its siblings:** scoping the sweep (the shipped sibling) narrows *which* queue is worked but still spends the firing on queue mechanics; ordering the buckets changes *sequence* but not *kind* of attention. This is the only candidate that changes the kind — it is the direct answer to "the hard problems never get sustained thought," not to "the sweep visits every branch."

**The known failure mode, inherited honestly:** this tree already measured roughly twenty scheduled passes that "produced commentary instead of structure." A firing licensed to think without clearing buckets is licensed to produce commentary. The assumption beneath is therefore about whether its output changes any decision, not whether it reads well.

## Definition of done

"A replayed firing reports a budget of its own and exactly one branch it spent on"

```
npx vitest run test/loop/per-firing-branch-budget.test.ts
```

Green means a firing declared as a deep-dive carries a budget scoped to itself, and its stored records (run ledger plus `.ost-agent/usage/events.jsonl`) resolve to exactly one named branch with no `git log` reading. Two separate gaps keep it red today. `LoopSpendSchema` only knows a whole-vault rolling window, and `UsageEvent` has no branch field. The spec is not written yet, so the first observation files as `no-spec`; the test node states both assertions a builder has to make true.

It settles only that a deep-dive can be audited. Whether its output changes any decision is "After three deep-dive firings the operator names a decision their output changed", and that needs a person. A green here must not be read as clearance to build.

The test title is quoted rather than wikilinked: its one backlink belongs to its parent assumption.
