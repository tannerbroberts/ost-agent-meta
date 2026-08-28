---
type: AssumptionTest
status: unvalidated
source: 'TRANSCRIPT:8a9777ad-a1ca-47fc-ab8e-3bd4b001a5cd'
created: '2026-08-06'
evidence: observed
threshold: >-
  At least 90% of tree-derived search arguments in the recorded trace are
  expressible as literal lookups.
instrument: npx vitest run test/telemetry/search-literality-census.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/observed

**Lane: compute-only.** The searches are already recorded in the tool-invocation trace; this is a count over data on disk.

Take every search invocation in the trace and sort it on two axes at once, because the parent assumption turns on their interaction. First: does the argument need pattern semantics, or would a literal lookup have returned the same set? Second: did the argument originate in the tree — a title, a body phrase, a path read from frontmatter — or was it written by hand?

Report the four cells. The one that decides the design is hand-written-and-pattern versus tree-derived-and-pattern. If tree-derived arguments are overwhelmingly literal while hand-written ones are freely patterned, then the interface should be drawn on provenance rather than on literalness, and this solution wants rewriting along that line. If tree-derived arguments frequently need patterns too, a literal-only interface cannot cover the work and the candidate should lose to its siblings.

**Pre-committed bar:** at least 90% of tree-derived search arguments are expressible as literal lookups. Below that, a literal-only interface does not cover the work.

Committed before counting, and worth stating plainly: this pass already knows two of its own searches were structural patterns, so the assumption is under real pressure and the bar is not a formality.

**What a green run here does not settle.** The trace records searches that were *issued*, not searches that were wanted — a pass that avoided a pattern search because the last one failed is recorded as never having needed one, which biases the census toward the answer this solution wants. It also covers only searches over node text; the shell failures in the same opportunity, where a path was globbed or a flag read as a filename, are outside its scope entirely and are the sibling candidate's territory.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/telemetry/search-literality-census.test.ts` — No test files found, exiting with code 1
- 2026-08-06 **green** (exit 0) `npx vitest run test/telemetry/search-literality-census.test.ts` — Duration  2.67s (transform 40ms, setup 0ms, collect 2.47s, tests 6ms, environment 0ms, prepare 29ms)

## Issues
- 2026-08-28 2026-08-28 (unattended sweep, repo sight): this test's instrument has RUN AND GONE GREEN, and its finding was never read out. The instrument log records red (exit 1, "No test files found") then green (exit 0, 2.67s) on 2026-08-06, and `ost_read_repo` confirms test/telemetry/search-literality-census.test.ts is present at 21,854 bytes. But no result is recorded against this node's own pre-committed bar — "at least 90% of tree-derived search arguments in the recorded trace are expressible as literal lookups" — so the four cell counts the census computes have never been reported anywhere on the tree. A green exit code says the classifier works; it says nothing about which side of 90% the answer fell on, and the parent solution's build decision turns entirely on that. This is the cheapest outstanding ask in this branch, because the counting is already done and only the read-out is missing: `ost-agent result "Census the recorded searches and split them by whether their argument came from the tree" -v <supported|refuted|inconclusive> -n "<the four cell counts and the tree-derived literal percentage>" -b <you> -u "<what this run left uncovered>"`. Flagged rather than answered: recording a result is a human's call, this pass ran nothing, and the node's own prose warns that the trace records searches that were issued rather than searches that were wanted, which biases the census toward the answer its parent solution prefers.
