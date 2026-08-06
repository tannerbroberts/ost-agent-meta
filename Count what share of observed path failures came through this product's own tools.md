---
type: AssumptionTest
source: 'TRANSCRIPT:748498c4-31fb-4110-9012-464c441a463f'
created: '2026-08-06'
evidence: assertion
threshold: >-
  At least 40% of path-shaped failures in the captured transcript corpus arrive
  through tools this repository controls. Below 40% the solution is refuted as
  stated and must either narrow to a named subset or be dropped in favour of a
  sibling.
instrument: npx vitest run test/friction/path-failure-attribution.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The corpus is on disk under `.ost-agent/evidence/TRANSCRIPT_*.md` and the attribution is a string match on the tool name each friction event already records. This is a question about a file, not about a person.

**What it does.** Classify every path-shaped failure in the corpus — no such file, no matches, exit 128 outside a repository, permission denied on a path — by the tool that produced it. Split into tools this repository owns and tools it does not. Assert the owned share clears 40%.

**Why it is red today.** No attribution exists in the product; the friction adapter records the tool name per event and nothing aggregates them this way. This is the mildest red of the set — the data is present and only the computation is absent — and it is worth saying that plainly rather than letting the missing file carry the weight.

**One thing the count will get wrong, stated in advance.** A permission-denied on a path is arguably not a layout failure at all, and this sweep hit several of them. Whichever way the classifier treats them will move the number, so the spec should report both totals rather than pick one and hide the choice.

**What a green does NOT settle.** That better error messages change what a run does next. It establishes only that the messages this solution would improve are a large enough share to be worth improving — necessary for the solution and nowhere near sufficient.
