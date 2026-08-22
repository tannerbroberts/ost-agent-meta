---
type: AssumptionTest
source: 'agent-ideation:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At least 120 of the 363 currently-unmapped evidence ids appear in at least 1
  node body, and at most 5 of those hits sit in a sentence that distinguishes
  the node from the record rather than resting on it. Below 120 hits the
  candidate drains too little to be worth building; above 5 negations the
  silent-wrong-drain risk is real rather than theoretical.
instrument: npx vitest run test/evidence/prose-citation-mapping.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** Both halves of this test are computations over files already on disk — no person, no experiment, no elapsed time. That is what makes it worth doing before either sibling candidate is costed: it is the rare question on this tree that the vault can answer about itself in one run.

**What the spec must do.** Take the evidence ids the sweep currently reports as unmapped, scan every node body for each, and report two counts: how many ids appear at least once, and how many of those appearances are contrastive rather than corroborative. The second count is the one that needs care — a crude substring match answers the first question and cannot answer the second, and a test that reports only coverage would look like a pass while leaving the candidate's actual risk untouched.

**Why this is red today, stated honestly.** `test/evidence/prose-citation-mapping.test.ts` does not exist. This is a `no-spec` red, which means it fails for the same reason any unwritten spec fails and does not by itself distinguish this question from any other. This pass cannot author spec files, so a `no-spec` filing is the only red reachable from here — the mechanism is documented at length on "A pass that cannot see the repository cannot set an instrument at all". What makes this instrument usable anyway is the threshold above: `confirmPermit` keeps a permit across a `no-spec` run when the test is threshold-bound, so a builder who opens the empty file still has a fixed bar to build to and a definite answer to bring back.

**What a green run would NOT settle.** It measures only whether the citations are on disk and how they are worded. It says nothing about whether draining this queue is something the operator wants (see the parent opportunity's stated limits), nothing about whether a prose scan is the right *mechanism* versus the structured-field sibling, and nothing about the records that were correctly read and skipped — which are invisible to this test by construction and are the whole subject of the third candidate.
