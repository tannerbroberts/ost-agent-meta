---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Every out-of-scope input (sidecar path, traversal, non-node title) is refused,
  and every reserved section is returned labelled rather than inline. One served
  sidecar read, or one reserved section indistinguishable from prose, fails it.
instrument: npx vitest run test/tools/read-node-body-scope.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Drive the body read with inputs chosen to break its scoping. Ask it for a title that resolves outside the node set, for a path-shaped argument aimed at the vault's own `.ost-agent/` sidecar, and for a traversal that would climb out of the vault root — each must be refused rather than served. Then ask it for a node that carries `## Results` and `## Instrument Log`, and require those sections to come back labelled as reserved rather than inline with ordinary prose, so a caller cannot mistake a recorded result for material it may rewrite.

## What this does not settle

Only that the read can be confined. Nothing about whether callers use it before composing merged prose, and nothing about whether an operator storing customer quotes finds the wider read surface acceptable — that one is a question for people and is not answered here.

## Instrument grounding

Weak red: the spec file is absent, so this command fails because nothing is there rather than because a real module falls short. The pass that wrote it had no repository sight — `ost_read_repo` was refused for want of `product.repos` in `ost.config.yaml`, and direct filesystem access to the checkout was denied. The path follows the suite's observed convention. A pass with repo sight should re-point it at the module that actually resolves node titles and assert against that resolver's real behaviour. Tracked as "My instruments are red because a file is absent, not because the behaviour is".

## Lane

Not declared. The question is mechanical, but the lane is a human's to set with `ost-agent lane --set`; this node sits in the humans-required lane by default until then.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/tools/read-node-body-scope.test.ts` — No test files found, exiting with code 1
