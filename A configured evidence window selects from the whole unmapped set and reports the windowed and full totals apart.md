---
type: AssumptionTest
source: 'agent-ideation:2026-10-01-unattended-sweep'
created: '2026-10-02'
evidence: assertion
threshold: >-
  at least 1 USAGE record listed when 30 TRANSCRIPT records sort ahead of it and
  the window names USAGE, with 0 change to done
instrument: npx vitest run test/mcp/next-work-evidence-window.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

The fixture follows `test/mcp/next-work.test.ts` and `test/mcp/scoped-next-work.test.ts`. First `initVault`, then `writeEvidence` 30 `TRANSCRIPT:` records and 1 `USAGE:` record. The transcript records sort first, so with the cap at 25 the usage record is hidden today. Then write an evidence-window key naming the `USAGE:` prefix into the fixture's config and call `computeNextWork`. The spec should assert four things. The usage record appears in `unmappedEvidence`. The response reports a windowed total of 1 next to the full total of 31. `done` is the same value it would be without the window, so a window can't forge completion. With the key removed, the response matches today's output exactly.

**Pre-committed threshold:** at least 1 USAGE record listed when 30 TRANSCRIPT records sort ahead of it and the window names USAGE, with 0 change to done.

**What kind of red this is: `no-spec`.** The instrument tool won't accept a `-t` filter into an existing spec, so the only legal red is a spec file that doesn't exist yet, and that gives no build permit. The assertion is written out above so the builder starts from a definite failing case and not an empty file. The fixture is what goes red: no config key filters evidence today, so the usage record stays hidden behind the cap.

**What this does not settle.** A green run shows the window can be built at that seam without touching `done`. It doesn't show that an operator will ever move the window. That is the sibling assumption, answered from eight weeks of git history, and it is still the cheaper and more decisive test for this candidate.

Unvalidated. Agent-proposed 2026-10-01; nobody has run it.

## Instrument Log
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-02 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-03 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-04 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-05 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-06 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-07 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-10-08 **no-spec** (exit none) `npx vitest run test/mcp/next-work-evidence-window.test.ts` — test/mcp/next-work-evidence-window.test.ts does not exist — no spec was collected, so nothing was measured
