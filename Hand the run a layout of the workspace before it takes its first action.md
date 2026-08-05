---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A map small enough to carry answers most of the lookups that were failing]]

At the start of every run, produce a compact map of what is actually here — the top levels of the tree, where the source is, where the tests are, where the vault is, which sibling directories exist — and give it to the run before it does anything. The information is cheap to gather, small to hold, and stable for the run's whole life.

The evidence makes the case precisely: one session missed `/Users/tanner/dev/ost-agent-meta` when the directory was `/Users/tanner/ost-agent-meta`. A one-line listing of what sits under the home directory would have made the guess unnecessary.

**Compared to the alternatives.** By far the simplest, and it front-loads a cost that is currently paid several times per session in failed calls. It is bounded — a map, not a full listing — and it becomes stale during long runs, though rarely in ways that matter. It cannot help with paths outside whatever the map covers, and choosing that boundary is the design question.

**What would make this the wrong pick.** A map large enough to answer every question is too large to carry, and one small enough to carry will omit the thing being looked for often enough that the probing habit persists. The failed probes then cost the same as before, plus the map.

## Definition of done

[[Draft the workspace map and check how many past failed lookups it would have answered]]

```
npx vitest run test/runner/workspace-map-coverage.test.ts
```

Green means a rendered workspace map that serializes under 2,000 characters answers at least 70% of the path lookups that actually failed in this vault's harvested transcripts. It is red today because nothing in the repository renders a workspace map at all.

**The size bound is half the assertion, not a formatting detail.** A map big enough to answer everything is too large to carry into every session; one small enough to carry will omit the thing being looked for often enough that the probing habit survives, and the failed probes then cost what they cost today plus the map. Asserting both clauses in one command is what keeps the solution from being trivially satisfiable by making the map bigger.

**What green does NOT settle.** It scores the map against paths that were reached for by a run that had no map, which is a corpus shaped by the absence of the thing being tested. It says nothing about staleness — a map handed over at the first action and wrong by the fortieth — and nothing about whether a run that is handed a map actually consults it rather than probing anyway.

## History
- 2026-08-05 unlinked [[Draft the workspace map and check how many past failed lookups it would have answered]] — moved under [[A map small enough to carry answers most of the lookups that were failing]] — the belief this test measures now has a node of its own
