---
type: AssumptionTest
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  Across 4 attempted dispositions — no node named, a node title that is not in
  the tree, a corroborates disposition naming a real node, and a reveals-no-need
  disposition naming nothing — exactly 2 are accepted and 2 are refused, and
  unmappedEvidence falls by exactly 1 per accepted disposition and 0 per refused
  one. If the reveals-no-need case is accepted while naming nothing, this test
  must report a refutation and not a pass.
instrument: npx vitest run test/evidence/dismissal-requires-a-node.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, guarding a safety property.** Whether a guard binds is a property of code, not an opinion, so this is settled by attempting the disposals and reading what comes back.

**What the spec must do, and why the fourth case is the point.** The first three cases are routine guard coverage. The fourth — `reveals no need`, naming nothing — is the case the parent assumption says will break the guard, and the threshold is written so that accepting it counts as a **refutation** rather than as three-out-of-four. That framing is deliberate: a guard which binds only where naming a node was easy anyway is not a mitigation of the objection this candidate carries, and a test scored on a simple pass rate would report it as one.

**Note what a refutation here means.** It does not kill the candidate; it collapses it onto its siblings. If the no-need case cannot be safely drained, this candidate loses the single advantage that distinguished it — draining records that were read and correctly skipped — and a human choosing between the three should then prefer whichever sibling is cheaper.

**Why this is red today.** `test/evidence/dismissal-requires-a-node.test.ts` does not exist, and no disposition mechanism exists to attempt these calls against. A `no-spec` red, with the usual weakness: it fails for the reason every unwritten spec fails. The threshold carries the definition of done.

**What a green run would NOT settle.** It shows the guard binds. It does not show the guard is *sufficient* — an agent that must name a node can still name a plausible-but-wrong one, and nothing mechanical distinguishes a considered corroboration from a convenient one. Whether an unattended actor should hold this power at all is the operator's decision and is named as such on the solution above; no exit code speaks to it.
