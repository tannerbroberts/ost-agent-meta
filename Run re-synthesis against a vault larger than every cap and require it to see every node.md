---
type: AssumptionTest
source: 'agent-ideation:2026-08-09-unattended-sweep'
created: '2026-08-10'
evidence: assertion
threshold: >-
  On a fixture vault of at least 1200 nodes, the re-synthesis input contains
  every node, or the run refuses and names the count it could not see. A run
  that silently returns a capped subset and labels its output a whole-tree
  re-synthesis fails the test. One silent truncation fails it.
instrument: npx vitest run test/ost/whole-tree-read-scale.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.**

**What this measures.** Whether the input to a re-synthesis pass is the whole tree or a capped sample wearing the name of one. Not whether the read is fast, and not whether the proposals are good — only whether the thing that claims to have read everything did.

**The assertion the spec makes,** written out so this is a designed test rather than a reserved path. Using the existing fixture helper at `test/ost/fixture-vault.ts`, and following the precedent already set by `test/ost/dedupe-scale.test.ts` for scale fixtures:

1. Build a vault of at least 1200 nodes — chosen because this live vault holds 1158, so the fixture has to exceed the size at which the caps are known to bite rather than a size someone hoped was safe.
2. Plant a distinguishing node deep in the alphabet, past where a 25-item or otherwise capped listing would stop. A duplicate pair is the sharpest choice: two nodes making the same claim, both placed beyond the cap.
3. Invoke the re-synthesis input path and assert **every** node id is present — specifically that the planted pair is in it. This is the assertion that goes red if the path routes through a capped reader.
4. Assert the negative case honestly: if the implementation declines to load a tree this size, the refusal must name the number of nodes it could not see. A refusal that says only "too large" fails, because a reader cannot tell a bounded gap from an unbounded one.

Point 3 is the load-bearing one. Point 4 exists so the spec does not force an unbounded read into a product that may reasonably choose to refuse — either behaviour is acceptable, silence is not.

**Why it is red today, and which kind of red.** A `no-spec` red, stated plainly. `test/ost/whole-tree-read-scale.test.ts` does not exist, and no re-synthesis module exists in `src/ost/` — verified by listing both this pass. So the command currently fails on the missing file, which the ruleset files as granting no build permit on its own. An unattended pass has read-only repo sight: it can name the module and write the assertion, and cannot leave the spec behind. The first builder act here is small, because the assertion is specified above.

**Why it is small.** One fixture builder that already exists, one generated vault, four assertions. No new dependency.

**What this does NOT settle, so a green is not over-read.** Passing proves the re-synthesis input is complete or honestly bounded. It proves nothing about whether reading the whole tree at once yields reorganisations a human accepts — that is the sibling belief on this solution, it names a person as the measurement, and it stays a human study. It also says nothing about cost: a read that is complete and takes an unacceptable amount of context to process would pass this and still be unusable, which is the trade-off the solution body names as "expensive in context and compute". And it says nothing about the real hazard the solution flags, that re-organisation is where an agent can silently destroy meaning.

⚠️ Unvalidated. Agent-ideated; no test was run and no result is recorded.

## Instrument Log
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/whole-tree-read-scale.test.ts` — test/ost/whole-tree-read-scale.test.ts does not exist — no spec was collected, so nothing was measured
- 2026-08-10 **no-spec** (exit none) `npx vitest run test/ost/whole-tree-read-scale.test.ts` — test/ost/whole-tree-read-scale.test.ts does not exist — no spec was collected, so nothing was measured
