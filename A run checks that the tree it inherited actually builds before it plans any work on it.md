---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Time the build check against how often a run would actually have found a broken tree]]

Before doing anything else, a run establishes whether the repository it has been handed is in a working state. If it is not, that becomes the report — this is broken, here is what is broken, here is the commit that broke it — and the run does not proceed to plan work on top of a foundation it knows is unsound.

This accepts that bad states will happen and makes them cheap to discover. The expensive part in the evidence was not the conflict; it was a session forming a plan, beginning work, and only then discovering that the ground had a hole in it.

**Compared to the alternatives.** The only option that protects against every way a tree can arrive broken, whatever caused it — a bad merge, a partial push, an interrupted rebase. It also costs a build on every run, which for a large project is a real tax paid mostly for nothing, and it comes too late to prevent anything.

**What would make this the wrong pick.** A run that stops because the tree is broken has produced nothing, and if the operator wanted it to fix such things, refusing to start is the opposite of useful. Whether a run may repair what it inherits, or must only report it, is a human's call.

## Definition of done

[[Time the build check against how often a run would actually have found a broken tree]]

```
npx vitest run test/loop/inherited-tree-build-check.test.ts
```

Green means a run refuses to plan against a tree that fails its own check, and the check costs less than the bound the test names. It settles feasibility and cost. It does not settle the trade the test is really asking about — whether broken trees are common enough to be worth paying that cost on every run — because the rate comes from history, not from the guard.
