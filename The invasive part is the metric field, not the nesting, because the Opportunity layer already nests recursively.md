---
type: Assumption
source: 'agent-ideated:2026-08-22-unattended-sweep'
created: '2026-08-22'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A sub-outcome metric survives a serialize round-trip, and no existing opportunity is re-parented to get one]]

**Feasibility assumption, stated so it can be false.** This node's prose calls itself "the most invasive option — it changes the schema and every existing node's ladder-up path." The belief recorded here is that the second half of that sentence is wrong and the first half is right about the wrong thing: the ladder-up path needs no change at all, and the only genuine schema change is a field to hold the metric.

**What the code shows, read first-party this pass (`src/ost/node.ts`, read in full).**

- **The nesting already exists.** `Layer` is a fixed union and `ost_create_node` enforces that an Opportunity attaches under the Outcome *or another Opportunity*. So a movable level between the root and the needs is already expressible — and already in use: this vault's own 37 category buckets are exactly that, generic Opportunities directly under the Outcome with the specific needs nested beneath them. Nothing in the tree would need re-parenting to gain an intermediate level, because the intermediate level is what the tree is already shaped like.
- **The metric does not exist, and cannot be smuggled in.** `OstNode` enumerates its fields: `status`, `source`, `created`, `confidence`, `evidence`, `lane`, `threshold`, `instrument`, `sight`. There is no metric or target. `threshold` is the nearest thing and is documented as an AssumptionTest field read by `askedOf`.
- **An unenumerated key is silently dropped on round-trip.** `serialize` writes only the enumerated keys into `data`, and `deserialize` lifts only the enumerated keys back off it. So a `metric:` added to a file by hand survives exactly until the next tool write of that node, and then vanishes with no error. That is the concrete cost, and it is small and specific rather than sweeping.

**Why this is worth writing down separately from the sibling beside it.** This solution's only other assumption is "Two practitioners place the same opportunity under the same sub-outcome" — a usability question about whether the layer is legible to people, correctly answered by people. This one is about what building it actually costs, and it is settleable by a spec. A builder handed only the usability question would price this against the node's own "most invasive" claim and scope it several times too large.

**Bearing on the unresolved duplicate beside it, stated without deciding it.** This node's Issues section records an unmerged possible duplicate — "Keep the goal I actually want as the outcome, and hang the affordable one beneath it as a milestone" — and names the deciding question as whether nesting is meant to be recursive. If the finding above holds, recursion is not what separates them, because recursion is already free; what separates them is whether the layer carries a metric. That reframes the human's question rather than answering it, and the naming decision stays theirs.

**What would make this false.** If a sub-outcome must be distinguishable from an ordinary Opportunity by every consumer — `check`'s `outcome-files-categories` rule, the rollup's bucket accounting, `evidenceExtents`'s `layer === "Opportunity"` filter — then it does need its own `Layer` member after all, and every one of those consumers is a change. That is the version of the claim this node's prose was reaching for, and the test beneath should find out which version is true.

_Method: first-party `ost_read_repo` of `src/ost/node.ts`, read in full (`truncated: false`), plus the `ost_create_node` hierarchy contract held this pass. Consumers named in the last paragraph were not re-read this pass. Nothing executed. Grounds feasibility only. Rung stays at the `assertion` floor._
