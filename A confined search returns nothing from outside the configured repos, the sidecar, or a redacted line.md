---
type: AssumptionTest
source: 'agent-ideation:2026-09-08-unattended-sweep'
created: '2026-09-08'
evidence: assertion
threshold: >-
  zero results returned from outside product.repos across all three escape
  cases, and zero unredacted secrets in returned lines
instrument: npx vitest run test/product/repo-search.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**Risk category: feasibility.** This is a question about this repository's code and nobody's opinion, which is why it carries a command instead of a person.

**What the spec must assert**, stated here so the command is a definition of done rather than a filename. Against a fixture vault with one configured repo, a sibling directory outside it, and a `.ost-agent/` sidecar inside it, a search for a string that occurs in all three returns matches from the configured repo only:

1. A match living outside `product.repos` is absent from the results — the escape is refused where it is *discovered*, not where it is named, which is the whole difference between confining a read and confining a scan.
2. A match inside the vault's own `.ost-agent/` sidecar is absent, matching the existing read's refusal of that path even when the vault is a configured repo.
3. A matching line containing a secret comes back redacted, in the same form the whole-file read redacts it — the case worth asserting because a redactor written for a whole file may behave differently on one line torn out of its context.

**Why it fails today, and what kind of red that is — said plainly rather than left for a reader to discover.** The spec file named above does not exist, because the surface that wrote this node can read the repository but cannot write to it. So this is a `no-spec` red: it exits non-zero for a reason that would be identical under any question written on that filename, and an empty file would turn it green. That is the weak kind of red, and it is recorded as such. What carries it is the pre-committed bar above — `src/eval/buildable.ts` keeps a weak red's build permit exactly when the test names a bound threshold, on the grounds that a builder who finds the path empty can still build to the number. The three assertions above are that number. **The first person to pick this up should write the spec, at which point the red becomes a red about behaviour and this paragraph can be struck.**

**What a green here would not settle.** That the verb is worth having, that anyone would use it, that the scan is fast enough for the wall-clock budget the sweep path runs under, or that string search is the right shape for the questions actually being asked. It answers confinement and confinement only. A passing spec here proves the code does what this node said; it never proves anyone wanted it, and desirability, viability and usability for this candidate sit exactly where they did before.

## Instrument Log
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-08 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-09-09 **no-spec** (exit none) `npx vitest run test/product/repo-search.test.ts` — test/product/repo-search.test.ts does not exist — no spec was collected, so nothing was measured
