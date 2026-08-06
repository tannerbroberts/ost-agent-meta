---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  All three resumed passes take the same next action the original took, with no
  work repeated and no state silently invented.
instrument: npx vitest run test/loop/pass-resume-fidelity.test.ts
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that everything a pass needs in order to continue can be written down at the handoff. If what the agent was holding cannot be reconstructed from the record, the resumed pass will either redo work or, worse, proceed on a wrong belief about where it got to.

**How it would run:** take three real passes that hit a wait, record their state at that point, end them, and start fresh passes from the record alone. Compare what each resumed pass does next against what the original pass did after its wait finished.

**What counts as failure:** not just an error, but a resumed pass that quietly starts from a different understanding than the one that stopped. That is the expensive outcome and it will not announce itself, so the comparison has to be against what the original actually did next, not against whether the resumed pass looked healthy.

Proposed by the agent; a human runs it and records the outcome.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/pass-resume-fidelity.test.ts — The threshold — all three resumed passes take the same next action the original took, with no work repeated and no state silently invented — is settled against recorded state rather than against anyone's afternoon: the spec drives three passes to a wait, serializes the handoff record, starts fresh passes from that record alone, and asserts each one's next action matches the original's while re-doing nothing. It fails today because a pass has no handoff record to resume from.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/loop/pass-resume-fidelity.test.ts` — No test files found, exiting with code 1
