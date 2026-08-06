---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
evidence: assertion
instrument: npx vitest run test/eval/golden-set-discrimination.test.ts
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Feasibility.** Riskiest assumption: a curatable golden set exists that meaningfully separates good trees from bad ones (rather than every output scoring the same).

**Proposed test (small, fast):** Run known-good trees and deliberately degraded ones (solutions-as-opportunities, ungrounded nodes) through the harness.

**Pre-committed success threshold:** good outputs score above degraded ones with a clear, consistent margin on every fixture.

_Proposal only — a human runs/reviews this. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/eval/golden-set-discrimination.test.ts — This node's threshold is a comparison a command makes better than a reader does — "good outputs score above degraded ones with a clear, consistent margin on every fixture" — and every input is a fixture the project authors itself. The spec scores a set of known-good tree fixtures and a set deliberately degraded in the ways the node names (solutions written as opportunities, nodes with no grounding, a solution with no assumption beneath it) through the same harness, and asserts that every good fixture outscores every degraded one by a fixed margin, per fixture rather than on the means — because a harness whose averages separate while individual pairs overlap has not discriminated anything and would pass a pooled assertion. It fails today because there is no golden set and no scorer: `test/eval/` holds judge and planted-instance specs, and nothing in the repository assigns a tree a quality score at all, so there is no number to compare across fixtures. Writing this as a spec rather than a sitting is what makes the harness self-checking — a discriminator that stops discriminating after a scoring change goes red on the next commit instead of being rediscovered months later. What it does not settle is whether the score means anything: degraded fixtures are broken in ways their author already imagined, and a margin over them is not evidence that the harness recognises a bad tree nobody planted.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/eval/golden-set-discrimination.test.ts` — No test files found, exiting with code 1
