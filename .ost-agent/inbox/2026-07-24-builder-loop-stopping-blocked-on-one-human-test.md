# Builder report: the loop is stopping itself — every solution is blocked, and only a human can unblock it

Filed by the builder loop, 2026-07-24, at the end of its fifth pass.

## What was built this pass

`ost-agent result "<test>" --verdict ... --note ... --by <who>` — the human's half of the evidence
gate. The gate built last pass blocks all 24 solutions, and nothing could ever clear it: the agent
may not run tests or record results, and no path existed for a human to record one. A gate nobody
can pass is a stop sign, not a gate.

Constraints that keep the channel honest: attribution is required (a result with no name on it
cannot be told apart from a fabricated one); the command is CLI-only, on neither the tool allowlist
nor the MCP surface, with a guard test that fails if any future tool exposes it; and writes only
grow a single `## Results` section, so a later run never replaces an earlier one.

**The builder ran no assumption test and recorded no result.**

## Why the loop is stopping rather than building a sixth thing

State of the tree after five builder passes:

- 24 solutions, **0 tested**, 24 proposed-only. Every candidate is BLOCKED by the gate.
- The thinker has committed nothing in four consecutive passes; 7 evidence items sit unmapped.
- Four of the five things this loop built are themselves solutions in this tree — each shipped
  before its assumption test was run.

Building a sixth solution would be the exact behavior the tree diagnoses under *"Building crowds out
the search for better evidence"*, committed by the loop that just built the instrument for catching
it. The binding constraint is no longer engineering capacity. It is that **nobody has run a single
assumption test**, and by this system's own rules no agent may run one.

## The one action that unblocks everything

The cheapest test in the tree is `Hand-distil three past sessions` — half a day, retrospective, no
build, and its threshold is already partly answered by the transcript harvester's real output
(3 mechanically-found items, all shell-quoting mistakes, 0 that a human would likely call product
evidence). A human rating those three sessions by hand would settle it.

Recording it takes one command:

```
ost-agent result "Hand-distil three past sessions" \
  --verdict supported|refuted|inconclusive \
  --note "<what actually happened>" --by "<who ran it>" \
  --evidence observed --vault ~/ost-agent-meta
```

After that, `ost-agent gate "Post-session transcript harvester"` clears, and a builder loop has
something it can honestly build against.

## Open questions for a human

1. Should the builder be hard-blocked by the gate, or allowed to proceed while blocked as long as it
   says so? Five passes of evidence suggest a soft gate gets ignored — including by an agent that
   had just written it.
2. The thinker has been idle all afternoon. If the two loops are meant to run together, the
   cartographer side is not running, and the map has not moved since the first pass.
