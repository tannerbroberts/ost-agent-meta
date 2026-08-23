---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Both merge shapes agree on every inbound edge, outbound edge, carried reserved
  section and refusal across all four fixture cases. Any single divergence
  outside the survivor's prose fails it.
instrument: npx vitest run test/tools/merge-patch-parity.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Build a fixture tree with the cases that matter — a loser with several inbound edges, a loser with outbound edges the survivor lacks, a loser carrying `## Results` and `## Instrument Log`, and the refusal case where the loser holds a recorded result and the survivor has none. Run each through the replace-shaped merge and through the patch-shaped merge, and assert the two agree on everything except the survivor's prose: identical inbound repointing, identical outbound union, identical reserved sections carried across, identical refusal on the gate-clearing case.

The refusal case is the one to watch. A patch form that forgot it would look correct on every structural assertion and would quietly hand solutions results nobody produced on them.

## What this does not settle

Nothing about readability of stapled prose after repeated merges, and nothing about whether a caller can correctly identify the loser's unique contribution — that is a judgement about writing, not a property of the mechanics.

## Instrument grounding

Weak red: the spec file is absent, so the command fails for want of a file rather than against a real module. Written without repository sight (`ost_read_repo` refused for want of `product.repos`). A pass with repo sight should re-point it at the existing merge implementation and its current test fixtures so the assertions run against real behaviour. Tracked as "My instruments are red because a file is absent, not because the behaviour is".

## Lane

Not declared. Mechanical question; the lane is a human's to set with `ost-agent lane --set`.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/tools/merge-patch-parity.test.ts` — No test files found, exiting with code 1
- 2026-08-23 **green** (exit 0) `npx vitest run test/tools/merge-patch-parity.test.ts` — Duration  564ms (transform 214ms, setup 0ms, collect 305ms, tests 42ms, environment 0ms, prepare 40ms)
