---
type: AssumptionTest
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-21'
evidence: assertion
threshold: >-
  With a concurrent firing holding either loop's lock, 0 of 3 reset attempts
  (clean branch, dirty tree, staged work) may discard its uncommitted work —
  each must refuse and say which lock blocked it; with no lock held, the reset
  runs and leaves the checkout on main.
instrument: npx vitest run test/loop/pre-firing-reset-safety.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

The parent assumption is that a hard reset before every firing cannot clobber a still-running firing. Repo sight this pass says the premise it rests on is false as stated, so this test is written to make the reset *safe* rather than to confirm it already is.

**What the repository shows, and it cuts against the parent solution.** Two firings can be live at the same time, by design, and they deliberately do not coordinate. `examples/automation/build-pass.sh` keeps its own `mkdir`-based lock under `$OST_BUILD_STATE`, outside the vault, and its comments are explicit that this is *not* `ost-agent loop due`: "That machinery is per-vault and single-tenant... Two loops sharing it would each see the other's firing as their own." Elsewhere in the same file, on why it stages one named file rather than `git add -A`: "The discovery loop may be mid-firing in the same vault — the two hold separate locks and neither waits on the other."

So at any moment the build loop and the discovery loop may both be running against the same checkout, with no mutual exclusion between them. A `git reset --hard origin/main` issued by one at its entry point is therefore able to discard the other's in-flight work, and nothing today would stop it. The parent assumption is not merely untested — the mechanism the solution proposes is unsafe against the concurrency the repository already documents.

**A second hazard in the same file.** The build loop's lock has a TTL: a lock directory older than `OST_BUILD_LOCK_TTL_MINUTES` (default 60) is broken on the grounds that the prior firing is "assumed dead". A firing that is merely slow rather than dead is therefore already exposed to a second firing starting beside it, and a reset at that second firing's entry point would land on the first one's live working tree.

**Pre-committed bar, fixed before anything runs.** Three cases with a concurrent firing holding a lock — a clean transient branch, a dirty working tree, and staged-but-uncommitted work. In all three the reset must refuse and name which lock blocked it; zero may discard the held firing's work. Both locks count: the build loop's `mkdir` lock and the discovery loop's own. With no lock held, the reset must run and leave the checkout on `main`, so the spec fails a reset that has been made safe by being made inert.

**What a green here does not settle.** It does not rescue the parent solution's central claim. The node's own body concedes it "does not stop a build session from editing a script mid-session and running the edited version within its own firing", and a lock-aware reset does not change that. It also says nothing about the TTL: a reset that respects a live lock still runs after a slow firing's lock has been broken at sixty minutes, and whether that window is acceptable is a judgement about the operator's real firing durations, not a fact in the repository.

**Worth a human's eye alongside this.** The parent solution carries two assumptions whose wording is very close — "doesn't clobber a still-running firing's in-flight work" and "never discards in-flight work a concurrent firing depends on". They may be one belief written twice. The duplicate scan reports sibling *opportunities*, not sibling assumptions, so nothing flags it automatically.

**Instrument honesty, stated rather than hidden.** This is a `no-spec` red: `test/loop/pre-firing-reset-safety.test.ts` does not exist, so the command fails today for the weakest available reason. Forced rather than chosen — `ost_set_instrument` accepts only a bare `npx vitest run <path>.test.ts` and refuses any test-name filter, so an assertion-specific red inside an existing spec cannot be expressed on this surface (measured this pass; recorded on "My instruments are red because a file is absent, not because the behaviour is"). The path sits in `test/loop/` beside `lock.test.ts` and `firing-residue.test.ts`, both of which already drive the locking and working-tree machinery this spec needs.

⚠️ Proposed only — the agent does not run tests or record results.

## Instrument Log
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/pre-firing-reset-safety.test.ts` — test/loop/pre-firing-reset-safety.test.ts does not exist — no spec was collected, so nothing was measured
