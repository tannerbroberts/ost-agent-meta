---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Seeing a path instead of a taxonomy changes which work a builder starts on]]
[[A credible route can be computed from the tree's own edges]]

Render the tree as a route rather than a hierarchy: given the current state and the goal state, display the specific chain of targets that would connect them, with the tradeoffs at each fork made visible. The underlying nodes are unchanged; what changes is that a reader sees a path instead of a taxonomy.

**Contrast with siblings:** Purely additive and the only option that requires no new declarations on any existing node — but it can only display an ordering the data already supports, so if nothing in the tree encodes altitude it will draw a confident-looking line through unrelated work.

**Provenance caveat:** Founder-stated in a single spoken rant, not sourced from a story-based customer interview. Believability rests on the floor rung (`assertion`). This is a hypothesis about a need, not an observed need; a human should confirm or discard it against real customer conversations before anything is built off it.

Evidence: `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Does a route view change which work a builder picks up first" — moved under "Seeing a path instead of a taxonomy changes which work a builder starts on" — the belief this test measures now has a node of its own

## Issues
- 2026-08-06 2026-08-06 In `solutionsMissingInstruments`, and an instrument would be a category error as this node stands. Its single Assumption child is "Seeing a path instead of a taxonomy changes which work a builder starts on" — a behavioural claim about what a builder does differently, which no exit code observes. Note that the sibling test "Produce three routes for one live branch and have a reader rank them without seeing the labels" already carries `npx vitest run test/ost/routes-with-forecloses.test.ts`, so route-shaped feasibility is instrumented elsewhere in the tree; what is missing here is not a command but the recognition that this node's recorded belief is about a person. For a human: flag humans-required, or add a feasibility Assumption (that a credible route can be computed from the tree's own edges) and instrument that, leaving the behaviour-change claim to observation of real builders. Recorded alongside the census on "Filter the queue on shipped and count what is still unsatisfiable"; `ost_flag_humans_required` is withheld from the unattended surface, so this pass could name the class but not label it.

## Definition of done

"Compute a route over a tree that encodes no ordering and require a refusal"

```
npx vitest run test/ost/route-from-edges.test.ts
```

**This covers the feasibility half only.** The command settles whether a credible route can be computed from the edges the tree already holds, and — the load-bearing part — whether the computation declines when those edges encode containment rather than sequence. It does not settle this node's other belief, "Seeing a path instead of a taxonomy changes which work a builder starts on", which names a builder as the measurement and stays a human study. Passing the command and shipping on it alone would mean building a correct route view without knowing whether a route is what anyone wanted.

**Why this appears now, on a node that carried no command for weeks.** A 2026-08-06 note in the Issues section below diagnosed the problem exactly — this solution's only recorded belief was behavioural, so the instrument queue was asking for a command that should never exist — and recommended adding a feasibility assumption and instrumenting that instead. It could not act, because the product repository was unreadable from the unattended surface and the fix depends on naming the module that would have to change. `product.repos` was configured on 2026-08-09 and repo sight now works, so the recommendation was carried out this pass rather than restated. The full account of that change, including what it does and does not unblock, is on "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed".

The red is a `no-spec` red and the test node says so; the assertion the spec must make is written out there, so the builder inherits a designed test rather than a blank file.
