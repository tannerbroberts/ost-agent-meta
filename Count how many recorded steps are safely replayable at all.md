---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 60% of recorded steps from the last 30 days classify as
  side-effect-free by a fixed rule, with no case-by-case judgement.
instrument: npx vitest run test/loop/replayable-step-share.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Replay executes something. The solution is only safe if the set of steps that can be re-run without consequence is large enough to be worth building for, and — more importantly — identifiable by a rule rather than by a judgement the tool does not have.

**The test.** Pull every recorded step from the last thirty days. Write the rule first, before looking at the distribution: a step is replayable if its command is on a fixed allowlist of read-only verbs (`vitest`, `tsc`, `ost-agent check`, `git status`, and similar). Then apply it and count. Steps that need a human to decide are counted as failures of the rule, not as passes.

**Why the rule comes first.** Deriving the allowlist from the sample and then measuring the sample against it would prove nothing. Pre-committing the rule is what makes the number mean something.

**Why 60%.** Below that, replay covers a minority of failures and the more portable "Snapshot the resolved environment, but only for the step that failed" is the better bet. Above it, replay covers the common case and the narrow version named in the solution body — replay only steps the loop itself issued and already knows to be read-only — becomes worth building.

**What it does not settle.** Whether an operator would close a failure on a replay result rather than re-running by hand anyway. That habit is the value this solution claims to recover and it needs a person to answer, which is why it is not folded in here.

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/loop/replayable-step-share.test.ts — Applies the fixed read-only-verb allowlist the node insists be written before looking at the distribution to every recorded step from the last thirty days, counting steps needing a human decision as failures of the rule, and asserts the node's 60% bar. It fails today because no allowlist is committed and nothing classifies recorded steps for replayability.

## Instrument Log
- 2026-08-04 **red** (exit 1) `npx vitest run test/loop/replayable-step-share.test.ts` — No test files found, exiting with code 1
