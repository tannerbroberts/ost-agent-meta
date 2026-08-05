---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
evidence: assertion
instrument: npx vitest run test/adapters/digest-delivery.test.ts
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability):** Stakeholders keep reading the digest and acting on it after the novelty of week one wears off.

**Proposed test:** Send a hand-written digest — no automation needed — after each pass for three weeks to five stakeholders. Track opens and, more importantly, human actions attributable to it: a test run, a decision made, a question asked back.

**Size:** three weeks of writing a few lines by hand. Deliberately manual: if a hand-written digest is ignored, an automated one will be too.

**Pre-committed threshold:** week-three open rate ≥60% AND ≥1 attributable human action per week in weeks two and three. Week one is discarded as novelty.

**Decides:** whether push beats pull for this audience, versus the rendered view and the ask-anything sibling.

Proposed by the agent — to be run by a human with real stakeholders. No results recorded here.

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 instrument: (none) → npx vitest run test/adapters/digest-delivery.test.ts — Engagement cannot be measured over three weeks if the digest never reliably arrives, and nothing today delivers one anywhere. This asserts delivery: a digest is produced on the configured cadence, is pushed to the configured stakeholder channel rather than left in the vault, names what changed since the previous digest rather than restating the whole tree, and a cadence that elapses with no digest sent is reported as a miss rather than passing silently. Missing-spec red, not assertion red — no digest or delivery path exists, so the command fails on a missing file; a builder should write it against the real adapter so it goes red on a skipped cadence. It does not settle engagement, which is what stakeholders do with the digest once it lands, and that needs three weeks and real people.
