---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Draft the workspace map and check how many past failed lookups it would have answered]]

At the start of every run, produce a compact map of what is actually here — the top levels of the tree, where the source is, where the tests are, where the vault is, which sibling directories exist — and give it to the run before it does anything. The information is cheap to gather, small to hold, and stable for the run's whole life.

The evidence makes the case precisely: one session missed `/Users/tanner/dev/ost-agent-meta` when the directory was `/Users/tanner/ost-agent-meta`. A one-line listing of what sits under the home directory would have made the guess unnecessary.

**Compared to the alternatives.** By far the simplest, and it front-loads a cost that is currently paid several times per session in failed calls. It is bounded — a map, not a full listing — and it becomes stale during long runs, though rarely in ways that matter. It cannot help with paths outside whatever the map covers, and choosing that boundary is the design question.

**What would make this the wrong pick.** A map large enough to answer every question is too large to carry, and one small enough to carry will omit the thing being looked for often enough that the probing habit persists. The failed probes then cost the same as before, plus the map.
