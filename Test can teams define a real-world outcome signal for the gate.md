---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-dogfooding-idea.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #ported-from-ost-agent-vault #evidence/assertion

**Risk category: Viability.** Riskiest assumption: teams can actually define and feed an external real-world signal that a gate can consume to decide outcome achievement.

**Proposed test (small, fast):** With ~3 teams, have each name the external metric/signal for their outcome and confirm it can be wired as the gate input.

**Pre-committed success threshold:** 3 of 3 teams define a usable, feedable outcome signal.

_Proposal only — a human runs this with real teams. Unvalidated._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-06 Lane finding, unlabelled because the label was refused. This test is humans-required and should carry the marker: its own method names outside people as the measurement — "With ~3 teams, have each name the external metric/signal for their outcome" — and its closing line is "a human runs this with real teams". Whether a team can name a signal it will actually feed is a fact about that team; no spec file substitutes. This pass attempted `ost_flag_humans_required` and was denied the tool ("you haven't granted it yet"), so the frontmatter still has no `lane:` and the test continues to look runnable to anything that reads the field rather than the prose. A human should run `ost-agent lane` to set it. Until then, treat the absence of a lane here as "nobody could label it", not as "safe to automate".
