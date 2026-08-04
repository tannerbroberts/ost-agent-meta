---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  Every source found is watchable directly, or has a proxy costing under an hour
  to build.
instrument: npx vitest run test/loop/work-source-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that every meaningful trigger is observable. A woken loop that cannot see one source of work will sleep through it while looking perfectly healthy, which is a quieter failure than idling and much harder to notice.

**Risk category: feasibility.**

**Design.** Enumerate everything that has produced new work in this vault over the last month — inbox drops, transcript harvests, usage rollups, human results recorded, human promotions, rule changes, edits by another agent. For each, determine whether it can be watched directly, and if not, what the cheapest proxy would be.

**Why it is small.** A census over one month of history, no code, and it decides whether the approach is viable before a listener is written.

**What it will not cover.** A source that produced nothing last month is absent from the census and may be the one that matters. The enumeration is bounded by what happened, not by what can happen.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/work-source-census.test.ts — The threshold — "every source found is watchable directly, or has a proxy costing under an hour to build" — is a property of committed code: the spec enumerates every channel that can put new work in front of a pass (the six ingest adapters, plus the human-initiated mutations `result`, `promote`, `lane` and `retract`) and asserts each one exposes a watchable event source rather than only a poll. It fails today because nothing in the repository enumerates work sources and no channel exposes an event at all.
