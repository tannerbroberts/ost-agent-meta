---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
killIf: >-
  An audit of this vault finds no humans-required lane that was set by a human
  CLI call, so the distinction excludes nothing the bare field would not have
killBy: '2026-10-31'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Whether a lane was set by a human or asserted by an agent is decidable from what the node already records]]

**Variation dimension: bought-vs-built. Position taken: adopted from inside, as-is — the mechanism already exists in this codebase and is copied rather than designed.**

`trustsShippedStatus` in `src/eval/shipped-audit.ts` solves this exact problem for the `shipped` field, and `solutionsMissingInstruments` already calls it. Its rule, stated in the bucket's own doc comment: the exclusion "does not trust the bare field — `status: shipped` is agent-settable — only a promotion recorded in `## History` with reasoning attached leaves the queue." Apply the identical rule to lanes. A solution leaves the bucket when its tests' `humans-required` lane was set by a human's `ost-agent lane --set`, which writes a reasoned line into `## History`; a lane that arrived any other way keeps the solution in the queue.

**Why this position and not another.** Both siblings trust the frontmatter field. That field is agent-settable: `ost_create_node` takes a `humansRequired:` argument, so a pass that cannot think of a command can remove its own work from the queue by declaring the question needs a person — and nothing downstream can tell that from a judgement a human made. That is self-certification, it is the failure this whole product is built to refuse, and it is the same one `trustsShippedStatus` was written to catch on the neighbouring field. Buying the answer that already works here costs less than designing a new one and inherits an argument that has already survived review.

**Cheapest form.** A `trustsHumanSetLane(test)` beside `trustsShippedStatus`, reading the same `## History` for the same shape of reasoned transition, called from the same place in `solutionsMissingInstruments`. `test/ost/shipped-status-audit.test.ts` already pins the trusted set against code that exists; the lane version gets the parallel spec.

**What it deliberately does not do.** It does not re-file anything, does not age anything, and offers the operator no new queue. A solution whose lane an agent set stays exactly where it is today — visible and unclearable — because on this candidate's account that is the correct report: the agent asserted the lane, nobody ratified it, and the queue should keep saying so.

**What it gives up, plainly.** It is the only candidate that leaves the counter high. On a tree where every lane was agent-set at creation time, it excludes nothing at all and the operator's experience is unchanged until they start ratifying lanes by hand — work this candidate creates for them and the other two do not. It also adds a second History-parsing audit to a hot path already carrying one, and History parsing is the kind of thing that goes subtly wrong on nodes whose History was written by an older version.

**What would make this the wrong pick.** If the operator has no appetite for ratifying lanes one at a time, this is a queue that stays red forever with extra machinery behind it — strictly worse than the filter. Its whole value depends on a human being willing to make the call it insists on.

**Honest note on how this was ideated.** All three candidates under this opportunity were composed in one context by one author; this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.

## Definition of done

"A lane written by the CLI and one written by an agent's creation argument are told apart from the node alone"

```
npx vitest run test/ost/human-set-lane-audit.test.ts
```

The bar, pre-committed: at least 1 human-set lane recognised and 0 agent-set lanes accepted. A single agent-set lane getting through refutes this candidate outright rather than calling for a tighter matcher. Run this one before choosing between the three siblings — it is where this candidate most likely dies, it costs one spec, and a refuted verdict here is the strongest argument for the filter sibling.

The spec does not exist yet, so the command is red for the weak reason; the bound threshold above is what carries a builder across that gap.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.
