---
type: AssumptionTest
created: '2026-08-07'
evidence: assertion
threshold: >-
  Every converted criterion returns an identical verdict idle and under
  saturation, and still returns red when the guarded behaviour is regressed.
instrument: npx vitest run test/gate/operation-budget.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

Take the timing-sensitive criteria that currently exist, express each as an operation budget, and require the verdict to be a function of the code alone. The spec runs each converted gate twice — once on an idle process and once against a deliberately saturated one — and asserts the two verdicts are identical, then asserts each gate still fails when the guarded behaviour actually regresses, so that load-independence has not been bought by making the gate unfailable.

The second half is the part that matters. A gate that always passes is trivially load-independent, and a conversion that quietly produced one would look like success on the first assertion alone.

## Pre-committed bar

Both halves must hold for every converted criterion: identical verdicts under load and idle, AND a red verdict when the guarded behaviour is regressed. A single criterion that passes the first and fails the second means the conversion removed a guard rather than stabilising it, and the assumption is false.

## What this does not settle

Nothing about whether operators want gates expressed this way, whether the counting seam is maintainable, or whether criteria genuinely about human-perceived latency survive the translation — those stay open and this test is not evidence about them. It answers feasibility only.

## Lane

Not declared here. The question this test asks is mechanical and needs nobody outside the building, but the lane that decides whether compute may run it unattended is a human's to set with `ost-agent lane --set`, and prose is never promoted to a label. This node currently sits in the humans-required lane by default; a human who agrees the question is compute-only can move it.

## Instrument grounding — read before trusting this command

This instrument was written by a pass with no sight of the repository: `ost_read_repo` was refused for want of `product.repos` in `ost.config.yaml`, and direct filesystem access to the checkout was denied. It is therefore the weak kind of red — the spec file is absent, so the command fails because nothing is there, not because a real module falls short. The path follows the suite's observed convention (`test/<area>/<name>.test.ts`, run under vitest). A pass with repo sight should re-point this at the module that actually holds the timing criteria and re-word the assertions against it. Tracked as "My instruments are red because a file is absent, not because the behaviour is".

## History
- 2026-08-07 body edited — The original body opened with "**Lane: compute-only.**", which this surface has no power to make true. The node was created in the humans-required lane — an instrument does not move a lane, and only `ost-agent lane --set` does — so the declaration contradicted the node's own `lane:` field and would trip the lane-conflict rule. Replaced with a Lane section that says what is actually the case and leaves the label to a human.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/gate/operation-budget.test.ts` — No test files found, exiting with code 1
