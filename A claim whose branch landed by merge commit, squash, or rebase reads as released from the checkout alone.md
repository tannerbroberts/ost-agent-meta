---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  3 of 3 fixture repositories (branch landed by merge commit, by squash, by
  rebase) report the claim released within 1 call to liveClaims after the
  landing, and 1 of 1 fixture with the branch still open at 9 hours reports it
  held
instrument: npx vitest run test/loop/claim-merge-release.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec asserts.** Build three throwaway git repositories in a temp dir, each with a `main` and a feature branch carrying one commit, and land the branch three ways: `git merge --no-ff`, a squash (`git merge --squash` + commit), and a rebase onto main. Write a claim record for each branch via `claimWork` in `src/loop/claim.ts` with the branch name attached (the field the solution adds), then assert that `liveClaims` — extended to consult merge state — reports each claim released. A fourth fixture leaves the branch unmerged and sets the claim's `claimedAt` nine hours in the past; assert it is still `held`, which is the behaviour that distinguishes this from the TTL it replaces.

**Lane: compute-only.**

**Why it is red today, and what kind of red.** `test/loop/claim-merge-release.test.ts` does not exist — a **no-spec red**, declared as such; it mints no permit until the spec exists and fails on an assertion. Once written, the squash case is the one expected to fail first: `git branch --merged` answers by ancestry, and a squashed branch is never an ancestor of main. The nine-hour case fails today by design because `isLive` reads only `expiresAt`.

**What a green does NOT settle.** Whether an abandoned open branch should hold a claim forever (the stranding this trades for), whether the forge should be consulted instead, and whether the two already-recorded targets — never claimed — are helped at all. Feasibility of the read only.

## Instrument Log
- 2026-08-20 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-21 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-22 **no-spec** (exit none) `npx vitest run test/loop/claim-merge-release.test.ts` — test/loop/claim-merge-release.test.ts does not exist — no spec was collected, so nothing was measured
