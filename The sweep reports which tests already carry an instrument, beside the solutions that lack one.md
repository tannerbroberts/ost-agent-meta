---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[The instrument field fits in the sweep without displacing the work it reports]]

**The idea.** `ost_next_work` stops reporting only which solutions lack an instrument and starts reporting, for each test beneath them, whether it has one and what it is. The pass can then tell attachment from replacement before it composes the call.

**Why this shape.** The observed failure was not a bad decision, it was a decision made without the input. The pass picked a test by title, had no way to learn that title already carried a command, and found out from the success message. Nothing about the tool was wrong; the surface simply had no read that answered the question, and `ost_read_tree` returns titles, layers, statuses, tags and links but not instrument fields.

This is the cheapest of the three candidates and the only one that changes no write path, so nothing that currently works can break.

**How it compares to its siblings.**
- "Attaching an instrument to a test that has one is refused unless replacement is declared" stops the write instead of informing it. Stronger, and it costs a round trip every time the repair is legitimate.
- "Replacing an instrument preserves the old command and re-arms the permit if it is restored" accepts that the mistake will happen and attacks what it costs. It is the only one that helps the case that already occurred.

**Where it fails, stated so it can be judged.** Information is not a guard. A pass working a 62-item backlog under a token budget can be handed the field and not read it — and the failure mode is exactly the same, with the surface now able to say it was told. That risk is real enough that this should probably ship alongside one of its siblings rather than instead of one.

There is also a budget cost that is not trivial here: the sweep already truncates four lists at 25, and adding a per-test field to a report that names 337 tests makes the response bigger in the place it is already being cut.

**Cost.** A field in an existing response. Smallest of the three.

⚠️ Unvalidated. Agent-ideated from a first-party error made on this surface.

## Definition of done

"Carrying the instrument field pushes no visible entry out of the sweep"

```
npx vitest run test/ost/next-work-instrument-visibility.test.ts
```

Written without repo sight, so its first red is an absent file. The explicit-null clause is load-bearing: a field present only when set is indistinguishable from a field cut for room.

## The instrument layer, counted — and the count changes this node's cost argument, 2026-08-28

This node estimates its own cost against "a report that names 337 tests." That figure is stale. Counted first-party from the vault this pass:

| Population | Count |
|---|---|
| AssumptionTest nodes | 463 |
| carrying an `instrument:` | 343 |
| carrying a `lane:` instead | 52 |
| carrying **neither** | **68** |

So the response this node proposes to widen would name 463 tests, not 337 — a 37% larger denominator than the body assumes, in exactly the place the body identifies as the problem ("the sweep already truncates four lists at 25, and adding a per-test field to a report that names 337 tests makes the response bigger in the place it is already being cut"). The objection is stronger than written, not weaker.

**The number that actually matters for the sibling comparison, though, is 68 rather than 463.** The sweep's `solutionsMissingInstruments` stood at 64 solutions this pass, and 68 tests carry neither an instrument nor a lane. Those two figures agreeing to within a handful says the backlog is not a long tail of tests waiting for someone to write a command — it is a nearly one-to-one set of tests that have never been dispositioned either way.

**What a sample of them shows, and it bears directly on this node's premise.** This pass read seven of the solutions on that queue in full. Every one had already been adjudicated by an earlier sweep, and the adjudications fell into three kinds, none of which a per-test instrument field would have changed:

- **Genuinely humans-required** — willingness to pay, buyer identity, whether an operator would let a default stand. The tail of the neither-set is dominated by these; they are the oldest nodes in the vault.
- **Already shipped and pinned green**, so any instrument would pass on arrival and measure nothing.
- **About an artifact outside this repository** — the harness's own task list, the Monitor tool's grammar — where no spec in `test/` can reach the subject.

**This sharpens the node's own stated weakness into something measurable.** The body says "Information is not a guard… a pass working a 62-item backlog under a token budget can be handed the field and not read it." The sample suggests a harder version: for most of this particular backlog the pass did read enough, decided correctly that no honest instrument existed, and still could not record that decision — because the tool that labels a test humans-required is withheld from the unattended surface, and `ost-agent lane --set` is a human's CLI call. The queue therefore re-offers the same adjudicated items every firing. On that reading the binding constraint is a missing *write*, not a missing *read*, and this candidate addresses the read.

That does not retire this node. A sighted pass still cannot tell attachment from replacement without the field, which is the first-party error this node was ideated from and is untouched by the above. It does mean a human comparing these three siblings should weigh a fourth option that none of them is: letting an unattended pass record a humans-required disposition it has already reached.

**One case worth naming separately, because it is neither instrumentable nor unlabelled.** At least one test in the neither-set — "Does refusing a newline inside a wiki-link catch breaks nothing else catches" — carries a completed compute-lane run in its own body, against all three pre-committed bars, with the note that only a human's `ost-agent result` can record the verdict. It is not missing an instrument; it is missing a recording. A per-test field of the kind this node proposes would report it as bare, which is a fourth failure mode for whoever designs the field.

**Method and limits.** Frontmatter key counts with ripgrep across the vault's node files, 2026-08-28 unattended sweep; the seven-solution read is a convenience sample from the queue's alphabetical head and tail, not a random one, so the three-kinds breakdown is indicative and not a proportion. No product code executed, no test run, no status or rung changed by this pass.
