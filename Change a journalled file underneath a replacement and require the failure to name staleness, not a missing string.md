---
type: AssumptionTest
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Both arms must be right and neither may be silent: a replacement failing after
  the file changed is reported as stale-file, one failing on byte-identical
  content is reported as bad-quote, and an unjournalled file yields an explicit
  cannot-say rather than a guess.
instrument: npx vitest run test/runner/failed-match-attribution.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Three fixtures and a hash comparison. No person is the measurement here, and reaching for one would be spending an afternoon on a question that is settled by a spec file.

**What the command does.** Journals a read of a fixture file; in the first arm rewrites the file and attempts a replacement that no longer matches, requiring the report to say the file changed since the read; in the second arm attempts a replacement that never matched against untouched content, requiring the report to say the quote was wrong; in the third arm attempts a replacement against a file with no journalled read and requires an explicit inability to attribute, rather than either verdict.

**The third arm is the one that matters.** Two-arm versions of this test pass trivially by always answering "changed", which is why the assumption above is written about coverage rather than about accuracy.

**Why it is red today.** `test/runner/failed-match-attribution.test.ts` does not exist and there is no read journal for it to consult. A missing-file red, not an assertion red — repository reads were denied on this surface, so the spec could not be aimed at a named module that would have to change.

**Distinct from the host's read-before-write guard**, tested separately by "Auto-satisfy a read-before-write, then change the file underneath and require the write to still refuse". That one asks whether a write is refused. This one asks what the run is told once a write has already failed, and lives in this product rather than in the harness.

**What a green here does NOT settle.** Only that the attribution is correct when it speaks. Whether a correctly-attributed failure changes what an unattended run then does is untested, and whether any operator cares about the distinction is not a question a spec can reach.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/failed-match-attribution.test.ts` — filter:  test/runner/failed-match-attribution.test.ts
