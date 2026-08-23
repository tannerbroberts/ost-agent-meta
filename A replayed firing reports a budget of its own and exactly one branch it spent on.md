---
type: AssumptionTest
source: 'REPO:OST-Agent/src/telemetry/usage.ts'
created: '2026-08-23'
evidence: assertion
threshold: >-
  at least 1 of 1 replayed deep-dive firings reports a per-firing budget and
  resolves to exactly 1 named branch from stored records alone; today 0 of 1 do
instrument: npx vitest run test/loop/per-firing-branch-budget.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** drive one firing declared as a deep-dive against a named branch, then replay it from stored records alone — the run ledger and `.ost-agent/usage/events.jsonl`, with no `git log` and no human reading prose. **At least 1 of 1 replayed firings must report a budget belonging to that firing and resolve to exactly 1 named branch. Today 0 of 1 do.**

**Two assertions, and each fails today for its own reason.**

1. *Per-firing budget.* `LoopSpendSchema` declares only `ceilingWeightedTokens` / `windowHours` / `sessionsDir` — a rolling whole-vault window. The spec asserts a firing's stamped record carries a budget scoped to that firing; there is no field to read it from.
2. *Exactly one branch.* `UsageEvent` has no branch field, and `surface` reads `mcp` for every firing type. The spec asserts the replay resolves one branch and refuses when it resolves zero or many; today it resolves zero.

**Why this is red for reasons specific to this test.** Neither assertion is "the file exists" or "the loop ran." Both name a value that must appear in a stored record and does not, and either one alone would keep the spec red — so a builder who adds a branch field but leaves the budget global still sees it fail, and the failure names which half is missing. Change the question and the assertions change with it, which is what a missing-file red can never claim.

**What a green here does NOT settle.** Only that a deep-dive is auditable after the fact. It says nothing about whether analysis-only firings change any decision — the sibling assumption's test, "After three deep-dive firings the operator names a decision their output changed", is on the outstanding-asks queue and is a person's. A green here would make a useless deep-dive precisely as measurable as a useful one, and the tree should not read it as evidence for the solution's worth.

**One thing this deliberately does not require.** It does not ask that branch attribution be impossible to reconstruct by hand — it already is possible, through the node titles in commit messages. It asks that the reconstruction cost stop being the operator's hours.

**Why a new spec path.** `test/loop/` holds `spend.test.ts` and `spend-ceiling.test.ts`; both spec the rolling-window ceiling, and both are green. Pointing at either would meet `verifyInstrument`'s first-run green refusal and could never produce an observation.

_Grounded in first-party `ost_read_repo` reads of `src/config/schema.ts`, `src/telemetry/usage.ts` and `test/loop/spend-ceiling.test.ts`. Nothing executed. Rung stays at the `assertion` floor._
