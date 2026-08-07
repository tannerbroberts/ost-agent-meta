---
type: AssumptionTest
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
threshold: >-
  On every surface the pass runs on, the full required tool list is confirmable
  without invoking any listed tool. A single surface where it is not fails the
  test.
instrument: npx vitest run test/runner/tool-surface-preflight.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, and it is the assumption the existing evidence most directly threatens.** This solution needs a pass to detect its own tool surface *before* using it. Session `e42cd03d` suggests that is not the default: `Unknown skill: superpowers:subagent-driven-development` was only discoverable by calling it. If a capability's presence can only be established by invoking it, a preflight check is not possible and this whole candidate collapses.

**The test.** On each surface the pass actually runs on, attempt to enumerate the available tools and confirm the required list against it, without calling any of them. Record for each surface whether it worked. This is a pass/fail per surface, not a percentage — a preflight that works on two surfaces and silently under-reports on the third is worse than none, because it converts a loud absence into a false green.

**Why the threshold has no partial credit.** The whole value of this candidate is the guarantee. A probabilistic preflight is "A sweep that cannot read its subject reports a clean result" with extra steps.

**What follows from each outcome.** If enumeration works everywhere, this is cheap and should ship. If it fails on any surface, the honest fallbacks are to call one cheap known tool and treat its failure as the signal, or to move the check outward to "Have the scheduler verify the environment before it dispatches a run at all", which may have visibility the pass does not.

**Adjacent finding this test would produce for free:** an actual inventory of how the surfaces differ, which is direct evidence for "The same agent has a different tool surface on every surface I run it on".

Proposed, not run. Recording a result is a human's `ost-agent result`.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/tool-surface-preflight.test.ts — The threshold is pass/fail per surface with no partial credit — the full required tool list must be confirmable without invoking any listed tool, on every surface the pass runs on — which a spec settles directly by asking the preflight to enumerate each supported surface and asserting the required list is confirmed with zero invocations recorded. It fails today because no preflight exists, so a missing tool is discoverable only by calling it.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/runner/tool-surface-preflight.test.ts` — No test files found, exiting with code 1
