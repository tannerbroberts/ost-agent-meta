---
type: AssumptionTest
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
threshold: at least 10 distinct derived dates across the 62 currently ageless entries
instrument: npx vitest run test/ost/ask-clock-derived-fallback.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Two assertions, because this belief has two ways of being false and only one of them is about the mechanism working.

**The mechanism.** Seed a vault with a test carrying a dated `## History` lane line and no entry on the ask ledger. Assert the queue entry reports a non-null age, and that it is distinguishable from a filed one — a third state, not a bare number silently occupying the same field as a real filing. `src/knowledge/asks.ts` already establishes why the distinction has to be visible: it keeps `null` apart from zero because *"zero would read as fresh"*, and passing a reconstruction off as a record breaks the same guarantee one level up.

**The spread.** Run the derivation over this vault's own 62 ageless entries and count distinct dates. Fewer than ten and the derived ordering is nearly as flat as the one it replaces, which refutes the candidate on its own kill criterion rather than on the mechanism.

**The spec to write.** Fixture as in `test/ost/pending-ask-queue.test.ts` — `initVault`, injected clock — plus a node whose body carries a `## History` lane line and whose vault has no `asks.jsonl`. Assert non-null `ageDays` and the derived marker. The spread half needs a fixture of several such nodes with differing History dates; it is a property of the real vault, so a spec can only pin that the count is computed, and the number itself is a reading someone takes against this tree.

**Why this instrument is red today, stated honestly.** `test/ost/ask-clock-derived-fallback.test.ts` does not exist, so this is a `no-spec` red — it fails identically to any question that could have been written on that path, mints no build permit, and this test is unfinished until the file exists and an assertion in it fails. The instrument surface takes one bare spec-file command and refuses shell punctuation, so a `-t` filter against the existing queue spec was not expressible.

**What this does not settle, and it is the more important half.** Whether the derived dates are *correct*. A spec can prove a number appears and is labelled; only a person comparing derived dates against git history can say whether they reflect when anyone was actually asked. That check is the parent solution's kill criterion and is deliberately not automated here — an exit code that went green would otherwise read as "the dates are right" when all it saw was that dates exist.

## Instrument Log
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-01 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-02 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-03 **no-spec** (exit none) `npx vitest run test/ost/ask-clock-derived-fallback.test.ts` — test/ost/ask-clock-derived-fallback.test.ts does not exist — no spec was collected, so nothing was measured
