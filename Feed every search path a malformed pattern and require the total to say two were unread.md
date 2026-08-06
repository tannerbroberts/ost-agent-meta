---
type: AssumptionTest
status: unvalidated
source: 'TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18'
created: '2026-08-06'
evidence: observed
threshold: >-
  Reported total is 8 examined / 2 unread with both reasons named, and no call
  path yields a bare count without handling the unread case.
instrument: npx vitest run test/ost/unread-subject-propagation.test.ts
---
#AssumptionTest #unvalidated #evidence/observed

**Lane: compute-only.** Whether a distinction survives a call chain is decided by running the chain.

Drive a sweep over ten fixture subjects, two of which cannot be read for reasons drawn from this vault's own record rather than invented: one whose search pattern is malformed in the way `{Charge` was malformed, one denied at the filesystem in the way the product directory was denied. The other eight are readable and between them contain a known number of hits.

Require the sweep's reported total to distinguish three quantities: hits found, subjects examined, subjects unread. Eight examined, two unread. A total that reports ten examined is the bug this solution exists to prevent. A total that reports eight examined and stays silent about the other two is the same bug wearing better manners, and must also fail — silence about an unread subject is what produced the clean result in the first place.

Then the part that actually tests the parent assumption: assert the flattening path is absent, not merely unused. If a consumer can obtain a plain count from the search result without handling the unread case, the guarantee is a convention, and conventions in this codebase have a recorded history of not holding — the wrapped-wikilink rule exists because asking people to keep links on one line did not work.

**Pre-committed bar:** the reported total is 8 examined / 2 unread with both reasons named, and no call path yields a bare count without the unread case being handled.

**What a green run here does not settle.** It covers the mechanical path only. Every summary this pass wrote was composed in prose by a model, and nothing in a type system stops a sentence from saying "no issues found" over a subject that was never read. It also uses two failure modes chosen because they are on record; a third that nobody has hit yet will not be covered, and this test passing is not evidence that the unread state is complete.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/unread-subject-propagation.test.ts` — No test files found, exiting with code 1
