# Builder report: the evidence-debt gate is built, and it blocks everything this loop has shipped

Filed by the builder loop, 2026-07-24, after building **"Evidence-debt gate before building"**.

## The verdict on this tree

```
Solutions: 24  (untested 0, proposed-only 24, tested 0)
```

Every solution in this tree has exactly one proposed assumption test and zero recorded results.
Run against the three solutions this loop has built and committed:

- `gate: BLOCKED — "Post-session transcript harvester" — 1 proposed test, none run: Hand-distil three past sessions`
- `gate: BLOCKED — "In-the-moment friction events filed by the agent" — 1 proposed test, none run: Five-pass count of self-filed friction events`
- `gate: BLOCKED — "Believability ladder required on every node" — 1 proposed test, none run: Labelled-vs-unlabelled branch comparison`

All three were built before any assumption beneath them was tested. The gate now says so
mechanically, and it would have said so before each build if it had existed. This is the
opportunity's own claim — *"the asking loses to the building every single time, and I only notice
months later"* — reproduced inside the loop that is supposed to be fixing it, in a single afternoon.

## Evidence for the assumption test "Can riskiest-assumption-tested be judged mechanically"

Partial answer, from building it:

- **Mechanically judgeable:** whether *any* assumption beneath a solution recorded a result. The
  signal is unambiguous — a `## Results` section in the test's body, or a human moving its status
  off `unvalidated`. No interpretation required, no model needed.
- **Not mechanically judgeable:** whether the assumption that got tested was the *riskiest* one.
  That requires knowing which assumption, if wrong, kills the solution — a judgement about the
  world, not about the tree's shape.

So the test's underlying question splits cleanly in two. A gate can enforce the floor ("something
was tested") without any model; it cannot enforce the ceiling ("the right thing was tested"). The
threshold on that test should probably be rewritten to ask about the floor only, since that is the
part a machine can hold.

## A discipline change the builder is adopting

From the next pass on, this loop runs `ost-agent gate "<solution>"` before choosing what to build,
and records the verdict. It will still sometimes build while blocked — the tree currently offers no
cleared solution, so a strict gate would mean building nothing at all — but a blocked build will be
stated as a blocked build rather than passing silently. The honest framing: everything shipped so
far is a bet placed before its test was run.

## What a human should decide

1. Whether the builder should stop entirely until at least one assumption test is run. That is one
   command away (`gate` already exits non-zero); it is a policy call, not a technical one.
2. Which of the 24 proposed tests to actually run first. The gate can rank by debt, but not by
   risk — see above.
