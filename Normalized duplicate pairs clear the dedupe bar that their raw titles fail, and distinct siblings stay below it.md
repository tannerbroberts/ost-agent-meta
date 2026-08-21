---
type: AssumptionTest
source: 'agent-ideated:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
threshold: >-
  Over a fixture set of at least 8 human-judged pairs: every confirmed-duplicate
  pair scores above 0.50 after normalization having scored below 0.50 before
  (the observed case is 0.29), and 0 distinct-sibling pairs cross 0.50 after
  normalization. Both halves must hold — 8 of 8 duplicates lifted with 1 sibling
  false-positive is a fail.
instrument: npx vitest run test/ost/statement-grammar.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

Two-sided on purpose. A normalizer that rewrites every statement into the grammar's own vocabulary would raise *all* pair scores and look like a success against a one-sided bar, while making the dedupe screen useless — it would nominate every sibling as a duplicate. So the spec asserts the lift and the non-lift together, over pairs a human has already judged.

**What the spec asserts.** A fixture set of at least 8 pairs drawn from judgements the tree already holds: confirmed duplicates (pairs a human merged, or the identical-work-item pair the parent measured at 0.29) and confirmed-distinct siblings (pairs that passed Torres's test — a solution exists that addresses one and not the other). Score each pair raw and normalized with the repo's existing comparison. Assert every duplicate crosses 0.50 only after normalization, and that no distinct sibling crosses it at all.

**Where this hangs in the code.** `src/ost/dedupe.ts` and `src/ost/extent.ts` already exist and are already specced (`test/ost/dedupe.test.ts`, `test/ost/dedupe-scale.test.ts`, `test/ost/extent.test.ts`), so the comparison side is present. What is absent is the normalization step this solution proposes — there is no module in `src/ost/` that applies a controlled situation/struggle/progress grammar to a statement before comparison. That absence is the thing the test stakes a claim about.

**Honest about the kind of red this is.** `test/ost/statement-grammar.test.ts` does not exist, so the first observation files as `no-spec`, not `red`. It mints no build permit and this test is not finished until someone writes the spec and an assertion in it fails. That is forced by the grammar rather than chosen: `src/knowledge/instruments.ts` admits one form only, `npx vitest run <one-spec-path>`, and refuses shell punctuation — so an agent that cannot author files cannot reach a non-vacuous red for behaviour that does not exist. The finding is recorded in full on "A pass that cannot see the repository cannot set an instrument at all". The fixture pairs and the two-sided bar are the part that makes this a definition of done rather than a filename.

**What a green here does NOT settle.** Only that normalization does its mechanical job. It says nothing about whether a reader still recognizes their own need in the normalized wording — that is the sibling assumption beside this one, it needs actual readers, and it is the risk the parent solution names as the honest one. A normalizer that passes this test and fails that one has traded Torres's raw material for tidiness, and a green here must not be read as clearing the solution.
