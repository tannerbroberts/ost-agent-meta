---
type: AssumptionTest
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  All 4 refusals named in the positioning copy are bound to a guard that reddens
  when disabled; 0 unbound. Any refusal with no binding guard is struck from the
  copy before it ships
instrument: npx vitest run test/release/claimed-refusals-bound.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** all 4 refusals the positioning names are bound; 0 unbound. A refusal that survives its guard being disabled is struck from the copy rather than explained.

**What the spec does.** Hold the claimed refusals as an explicit list in the spec — self-validation, outcome authorship, result recording, rung ceiling — each paired with the guard that makes it true and with the assertion that fires when the guard is gone. For each pair: exercise the refusal path and require it to refuse, then neutralise the guard in a fixture and require the same call to be *accepted*. A refusal that still refuses with its guard removed is not bound to it, and the pairing is wrong. The second direction is the whole test: without it, four assertions that the tool refuses things pass against a tool that refuses everything, and nothing has been measured.

The list is the deliverable as much as the assertions are. It is the thing a copywriter reads before adding a fifth sentence, and a fifth sentence with no pair in it is the failure this catches.

**Why it is red today.** `test/release/claimed-refusals-bound.test.ts` does not exist, so this is a `no-spec` red and is declared as one. The bound threshold above is what keeps it a working permit. The mechanism it would be red *about* is named and was read this pass: `test/release/withdrawn-claims.test.ts` implements exactly this shape for one *retired* claim, with its own anti-vacuity tests in both directions, so the pattern is proven in this repository and only the positive direction is missing.

**What this does NOT settle.** Whether anyone finds refusals attractive. A green here proves the four sentences are true and stay true; it is silent on whether a buyer reads them as trustworthiness or as the product being worse, which is the sibling assumption and is correctly a person's. It also does not judge whether these are the *right* four refusals to lead with — that is positioning judgement, and no exit code holds it.

⚠️ Unvalidated. Agent-designed; nobody has run it.
