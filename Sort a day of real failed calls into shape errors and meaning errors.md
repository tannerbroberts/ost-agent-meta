---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/telemetry/failure-shape-vs-meaning.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility** — how much of the real problem the shipped mechanism actually covers.

**The assumption under test.** That schema validation catches a worthwhile share of the calls that damage the vault. The node is honest that it checks **shape, not meaning**: a call with every field present and correctly typed but carrying the wrong node title, or an empty string, still writes. Since v0.17.0 shipped on the strength of one replayed call, the coverage question has never been sized — and the shipped state makes it *more* urgent, not less, because a validator that reports few problems reads identically whether it is catching everything or catching the easy tenth.

**The material is already on disk.** `USAGE:2026-07-26` records **93 calls, 62 failed** — the highest failure day in the trace, and the sampled failures are already visibly mixed: `ost_annotate: no such node: probe` and `no such node: x` are *meaning* errors (well-formed calls naming nodes that do not exist), while `ost_create_node: "undefined" needs an evidence class` is a *shape* error the schema layer catches. The classification this test asks for is the one that day's data was never put through.

**The test (pure replay, nothing runs against the vault).** Take every failed call in the append-only tool-invocation trace for 2026-07-25 through 2026-07-27 (217 calls, 62 failures). Classify each failure:

- **shape** — would be refused by schema validation alone;
- **meaning** — schema-valid, semantically wrong (nonexistent node, empty-but-typed string, wrong-but-well-formed title);
- **neither** — an environment, permission, or filesystem failure the validator was never aimed at.

**Pre-committed threshold.** **Shape errors at 50% or more of all failures** and the shipped validator stands as a substantially complete answer to its opportunity. **Below 50%** and the majority of real damage is semantic, and "A tool call I got slightly wrong destroyed the note I was filing" needs a sibling candidate aimed at meaning — an existence precheck on node titles, or a non-empty-content guard — rather than further schema work.

**What a result must also state.** How many of the 62 were self-inflicted probes rather than genuine attempts. A day where 75 of 93 calls were `ost_annotate` against titles like `probe` and `x` looks like someone testing the tool surface, and probe failures should be reported separately rather than either counted or quietly dropped — they inflate the denominator and they are not the failure mode this branch is about.

**Who runs it.** Mechanical classification, human verdict. This pass proposes the design only.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/telemetry/failure-shape-vs-meaning.test.ts — The node already describes the work as "mechanical classification" and its threshold is a share — shape errors at 50% or more of all failures — over calls that are already on disk in the append-only tool-invocation trace for 2026-07-25 through 2026-07-27 (217 calls, 62 failures). The spec replays those failures, classifies each as shape (refusable by schema validation alone), meaning (schema-valid but semantically wrong — a nonexistent node title, an empty-but-typed string), or neither (environment, permission, filesystem), asserts the shape share against the 50% bar, and reports the probe-inflated subset separately as the node requires, so `ost_annotate` calls against titles like `probe` and `x` cannot pad the denominator. It fails today because nothing classifies a recorded failure by kind — the trace stores the message and no code partitions it. What it does not settle stays exactly where the node put it: the verdict is a human's, and a shape share above the bar says the shipped validator is substantially complete for the failures that HAVE happened, not that semantic damage is rare.
