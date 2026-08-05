---
type: AssumptionTest
source: 'TRANSCRIPT:35566d8b-a635-49b1-acc8-6bfbeeb134e7'
created: '2026-08-05'
evidence: assertion
threshold: >-
  The narrowed rule covers all 4 captured failures, and no scaffold target in
  the record lies inside an existing repository.
instrument: npx vitest run test/runner/unconditional-scaffold-init.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

Two assumptions, and the test is worth running because they can disagree.

The first is that the **narrowed** rule is enough. The candidate's honest form is not "initialise unconditionally" but "initialise unconditionally in directories this tool created, and never touch one it did not" — because the broad form takes an unrequested action on the operator's disk, in a product whose trust story is that it does not do that. If the narrowed rule fails to cover the observed failures, the candidate only works in a form it should not ship in, and that is a kill.

The second is that initialising is **safe where it would run**. A `git init` inside a directory that is already inside another repository creates a nested repo that is genuinely confusing to unpick, and that is the concrete harm hiding behind "git init is basically harmless".

**Design.** For each captured failure, check whether the directory was tool-created (so the narrowed rule would have initialised it). Separately, walk every scaffold target in the record and check whether any lies inside an existing working tree. Both clauses must pass.

**Why it is small.** Both are properties of paths that are already in the record.

**What it will not cover.** Whether the operator *wants* their disk written to without being asked is a consent question, not a coverage question, and no count settles it. If a human's answer is that unrequested initialisation is unacceptable at any scope, this candidate is dead regardless of how green this comes out — see "Fear the agent could take a destructive, irreversible action".

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/runner/unconditional-scaffold-init.test.ts` — No test files found, exiting with code 1
