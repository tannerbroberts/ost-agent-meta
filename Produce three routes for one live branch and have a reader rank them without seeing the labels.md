---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The reader's risk ranking matches the assigned one, and they name at least one
  foreclosure per route that was also written down.
instrument: npx vitest run test/ost/routes-with-forecloses.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that three genuinely distinct routes can be produced, and that the risk levels assigned to them mean something. If two of the three are obviously worse, the whole thing is a recommendation in costume; if the risk labels are a model's invention with no basis, the operator is choosing between three fictions.

**Risk category: feasibility.**

**Design.** Take one live branch of the tree and produce the three routes. Strip the risk labels and the recommendation. Give the three to a reader who knows the domain and ask them to rank the routes by risk and say what each forecloses. Compare their ranking and their foreclosure list to the ones that were stripped out.

**Why it is small.** One branch, three short write-ups, one reader.

**What it will not cover.** Agreement between a generated risk ranking and one reader's is weak evidence that either is right. It would catch the worst case — labels that are noise — and would not establish that they are well calibrated.

A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/ost/routes-with-forecloses.test.ts — A reader cannot rank three routes blind unless three routes exist and are genuinely different, and nothing today produces any. This asserts what the ranking presupposes: a route request for one branch returns exactly three, each naming its risk level and — the part the solution is actually about — what choosing it forecloses, with the foreclosed sets differing between routes, so a route that forecloses nothing or repeats a sibling's trade-off fails. Missing-spec red, not assertion red: this pass holds no repo-read grant, so the file is absent; a builder should write it against the real route generator so it goes red on a route with an empty forecloses field. It does not settle the blind ranking, which needs a reader and stays with a human.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/ost/routes-with-forecloses.test.ts` — No test files found, exiting with code 1
