---
type: Assumption
source: 'REPO:OST-Agent/src/ost/node.ts'
created: '2026-08-23'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false.** This solution's own argument against itself is that "every node created before it is replaced ladders up to a goal nobody chose, and the believability ladder has no rung for 'mapped against a mandate that was not real'." That risk is survivable only if the damage is *identifiable* — if, once the operator runs `set-outcome`, the tree can say which nodes were written under the placeholder. If it cannot, a placeholder run leaves no way to separate the provisional from the real, and the node's sequencing warning ("cheapest to build, most expensive to be wrong about") understates the problem: being wrong would be undetectable rather than merely costly.

**It is false today, read first-party from source this pass.** `OstNode` (`src/ost/node.ts`) declares exactly these fields: `title, layer, status, source, created, confidence, evidence, lane, threshold, instrument, sight, tags, links, body`. **None of them records which mandate was in force when the node was written.** `created` is a calendar date (`isoDate`, `YYYY-MM-DD`), not a mandate generation, and `source` records where the evidence came from, not what the tree was aiming at.

The gap is not merely unfilled, it is closed by construction: `serialize` writes an enumerated key list, so a field nobody added to that list is dropped on round-trip. Recording this would be a schema change, not a convention — the same shape of finding already recorded on this tree for an unenumerated `metric:` field.

**The honest qualification, stated so the belief is not overstated.** A partial partition may be recoverable without a schema change: this solution's prose asserts that `set-outcome` "preserves the prior mandate in the root's history", so the replacement date would be readable from the root's `## History`, and nodes could be split by `created` against it. That degrades exactly where it matters. `created` is a date with no time, so every node written on the replacement day is unclassifiable — and a placeholder replaced on the day it was scaffolded is the *good* case this solution is designed to produce. So the cheap partition works only for the failure mode (a placeholder that sat for weeks) and not for the success mode.

**What this is not.** It says nothing about whether a loudly-marked placeholder actually gets replaced, which is the sibling assumption beneath this solution and is correctly a person's question about behaviour. This is the feasibility half: whether, after the fact, anyone can tell what was written under a mandate nobody chose.

_Method: first-party `ost_read_repo` of `src/ost/node.ts` and `src/ost/frontmatter.ts`, both read in full (`truncated: false`), plus a listing of `test/ost/`. Nothing executed; the `set-outcome` history claim is quoted from this solution's own prose and was NOT verified against the CLI this pass — `src/cli/index.ts` exceeds this surface's read cap. Rung stays at the `assertion` floor._
