---
type: AssumptionTest
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
threshold: >-
  0 solutions carrying a compute-runnable test are dropped, and at least 1
  all-cautious solution is
instrument: npx vitest run test/eval/lane-aware-instrument-bucket.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**The design.** Build a fixture tree with three solutions and run `solutionsMissingInstruments` over it. The first carries two tests, both `humans-required`, neither with an instrument — it must not be listed. The second carries two tests, one `humans-required` and one in a lane `computeMayRun` allows — it must still be listed, because a live path to a builder exists beneath it and a filter keyed on "any" rather than "every" would lose it. The third carries two tests with no lane field at all — the case the assumption names as the second way this goes wrong, since `computeMayRun` fails closed on a missing lane and would silently drop every pre-lanes solution in the tree. The spec asserts which of the three come back and pins the unlabelled case explicitly rather than letting it ride on the cautious default.

**Pre-committed bar, stated before running:** 0 solutions carrying a compute-runnable test are dropped, and at least 1 all-cautious solution is. A filter that drops nothing has not been built; a filter that drops the second solution is worse than no filter and the candidate should be refused rather than fixed, because losing a buildable solution silently is the failure the bucket exists to prevent.

**What kind of red this is, said plainly rather than left for the log to reveal.** `test/eval/lane-aware-instrument-bucket.test.ts` does not exist, so this command is red today for the weakest available reason — it would be equally red under any question written on that filename, and `runInstrument` will file it as `no-spec` rather than as a measurement. That is the strongest red this surface can author: writing the failing assertion requires a write grant on the product repository, which an unattended sweep does not hold and should not. The pre-committed bar above is what carries the builder across that gap, and it is doing real work here rather than filling a field — `confirmPermit` keeps a weak red's permit only when the threshold is bound, on the precedent of one complete lifecycle this vault watched succeed that way.

**What a green here does not settle.** Only that the filter behaves as specified against a fixture. It says nothing about whether the lanes on this vault's 488 real tests were set by anyone's judgement — the candidate that distrusts the bare field is built on exactly that doubt, and this spec is blind to it. It also says nothing about desirability or viability: nobody outside this project has been asked whether a quieter bucket is what they want.

## 2026-09-01 — the write grant is not the only thing standing between this surface and a strong red

Four lines, per this branch's convention. Only what is new, and it corrects one sentence above rather than adding a census.

**The claim being qualified.** The section above says the weak red is "the strongest red this surface can author: writing the failing assertion requires a write grant on the product repository, which an unattended sweep does not hold and should not." That is true and it is not the whole obstacle. A second, independent one sits in the instrument grammar itself, and nothing on this tree records it.

**Read first-party this pass from `src/knowledge/instruments.ts`.** `INSTRUMENT_FORMS` holds exactly one form, and its pattern is anchored end-to-end: `^npx vitest run (?<target>[A-Za-z0-9][A-Za-z0-9._/-]*\.test\.ts)$`. Nothing may follow the filename. Separately, `SHELL_METACHARACTERS` rejects `'` and `"` on sight. So the form the unattended sweep's own instructions hold up as the strong-red exemplar — an existing spec file narrowed by `-t "the assertion that must be added"` — is refused twice over by this product before it ever reaches a runner. It is not merely unwritten here; it is inexpressible.

**Why that changes the advice and not just the accounting.** A reader of the paragraph above would reasonably conclude that granting an unattended pass write access to the product repository closes the gap. It does not close it by itself. With the grammar as it stands, an instrument may name one whole spec file and nothing narrower, so the only strong red available to any author — granted or not — is a spec file that exists and whose assertions genuinely fail today. And a third mechanism narrows even that: `collectedNothing` in `src/ost/instrument.ts` matches "No test suite found in file" as well as "No test files found", so creating the file empty is classified `no-spec` too. The honest strong red is therefore a spec carrying a real failing assertion, or one importing a module the solution has not created yet — which that file's own comment calls "the commonest honest one in test-first work."

**What this does not establish.** It is a reading of two modules, not a run: nothing was executed and no observation was filed. It says nothing about whether the grammar *should* admit a filter — widening `INSTRUMENT_FORMS` is a real decision, and that file argues at length that a closed vocabulary is the anti-fabrication guarantee, since an agent that can write any string can write one that exits 0. A `-t` filter is not obviously safe under that argument: the filter text is author-chosen, and a filter matching nothing exits non-zero for a reason no more specific than a missing file. So this is a finding about why the exemplar cannot be followed here, offered to whoever weighs a grammar change, and not a request for one.

**Nothing else about this node changed.** Its instrument, its bound threshold, its design and its statement of what a green does not settle are all untouched.
