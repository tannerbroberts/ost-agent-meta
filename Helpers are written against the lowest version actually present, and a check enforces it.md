---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A floor can be picked that a linter can enforce and that covers the machines in play]]

Pick the floor deliberately — bash 3.2, because that is what macOS ships — and enforce it where the script is written rather than where it is run. A linter configured to that floor rejects `mapfile` and everything like it at authoring time, in the same place every other coding standard is enforced.

This moves the discovery to the earliest possible moment, which is neither install nor run but the commit that introduced the incompatibility, when the person who wrote it is still looking at it.

**Compared to the alternatives.** Catches the problem before it can reach any machine, needs no manifest to be maintained, and cannot be defeated by an undeclared dependency, since the linter reads what the script actually does. It constrains the author permanently to an old dialect, which is a real ongoing cost, and it protects only against version drift — a missing command that exists at every version is invisible to it.

**What would make this the wrong pick.** Choosing the floor is a guess about every machine the helper will ever run on. Set it too low and the code is worse than it needs to be forever; set it where the evidence pointed and the first Linux container with a different shell entirely is outside the guarantee.

## Definition of done

[[Run a bash 3.2 linter over every helper and count what it flags and what it misses]]

```
npx vitest run test/runner/helper-bash-compat-lint.test.ts
```

Green means a shell linter set to a bash 3.2 floor, run over every helper this project installs, flags the known `mapfile` use and raises at most 2 findings outside the committed expected set. It is red today because no linter is configured at a version floor and nothing runs over the helpers.

**The false-alarm count is the load-bearing half, not the catch.** Flagging `mapfile` is nearly certain — the linter reads what the script does rather than what someone declared, so it cannot be defeated by an undeclared dependency. What would actually kill this approach is a check people learn to ignore, and that is measured by the second clause. A command that asserted only the catch would go green while the mechanism was busy becoming furniture.

**What green does NOT settle.** The linter protects against version drift and nothing else. A command that is simply absent on the target machine — present at every bash version, just not installed — is invisible to it, which is the failure [[Installation runs the helper's own preflight and refuses to install what cannot run here]] exists to cover. Green here and a broken helper there are entirely compatible.

## History
- 2026-08-05 unlinked [[Run a bash 3.2 linter over every helper and count what it flags and what it misses]] — moved under [[A floor can be picked that a linter can enforce and that covers the machines in play]] — the belief this test measures now has a node of its own
