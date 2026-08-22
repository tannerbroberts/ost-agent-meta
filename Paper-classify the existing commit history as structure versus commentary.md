---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-24-external-review-five-dimension.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/loop/pass-shape-classifier.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility):** commentary-vs-structure is reliably detectable from commit contents alone.

**Method:** hand-label this vault's full commit history (structure = new nodes/links/status; commentary = annotations/appends only); apply the proposed classifier rule on paper to the same commits. Hours, existing data.

**Pre-committed threshold:** >= 90% agreement between rule and hand labels, else the idle-down trigger cannot be trusted and the solution is deferred.

**Decides:** build idle-down vs rely on the mark-acknowledged affordance to make done-ness reachable.

*Proposed by the agent-side hard-fix pass — to be run by a human. No results recorded here.*

## History
- 2026-07-24 evidence: (none) → assertion — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-05 instrument: (none) → npx vitest run test/loop/pass-shape-classifier.test.ts — Applies the structure-versus-commentary rule to a committed fixture of hand-labelled vault commits and asserts at least 90% agreement, which is this test's own pre-committed bar. Red today because no pass-shape classifier exists in the loop module at all — the rule ("new nodes/links/status" = structure, "annotations/appends only" = commentary) lives only as prose in the solution node, so there is nothing for the spec to import.

## What the instrument does not settle

`npx vitest run test/loop/pass-shape-classifier.test.ts` answers the feasibility question this test actually asks — can the rule reproduce a human's labels from commit contents alone — and nothing beyond it. A green exit says the classifier agrees with the fixture; it does not say the hand labels were right, and it does not say throttling on that signal is a good idea.

The solution's own stated failure mode survives a pass entirely: the tetrix builder briefing was commentary-only and was arguably the most valuable artifact of its run, so a classifier with 95% agreement would still have throttled after the best thing the agent did. Whether the signal should drive spend is a judgement about value, not about detection, and this instrument does not touch it.

The fixture's hand labels are a human input committed once. If they are re-cut, the instrument measures agreement with a different opinion and the number is not comparable across that change.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/loop/pass-shape-classifier.test.ts` — No test files found, exiting with code 1
- 2026-08-22 **green** (exit 0) `npx vitest run test/loop/pass-shape-classifier.test.ts` — Duration  247ms (transform 17ms, setup 0ms, collect 20ms, tests 7ms, environment 0ms, prepare 25ms)
