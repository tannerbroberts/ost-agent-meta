---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-29'
created: '2026-08-29'
evidence: assertion
threshold: at least 5 of the 8 recorded sightings wait on work the same session started
instrument: npx vitest run test/loop/wait-producer-census.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility.** A census over code and fixtures already on disk — no person, no interview, no afternoon.

**What is being counted.** Not the curated three in `WAITING_CASES`, but every blocked wait the corpus holds. `test/loop/wait-primitive-affordance.test.ts` already walks `test/fixtures/corrections/*.jsonl` through `corpusCommands()` and `corpusRefusals()`, and `src/loop/wait.ts` says in prose that there are eight sightings, six of them the CI-check shape. The census classifies each one: did the session that wrote the wait also start the thing it was waiting on?

**The assertion the builder has to write, named so the spec is not a blank page.** `WaitingCase` in `src/loop/wait.ts` has four fields — `id`, `intent`, `session`, `blocked` — and none of them records who started the work. There is nowhere in the type for the answer to live. So the build is: give `WaitingCase` a field classifying the producer as self-started or foreign, populate it for all eight sightings by walking the fixtures rather than by hand, and assert that at least five of the eight come back self-started. Read against today's `WAITING_CASES` the belief looks like it will be refuted — `ci-check` runs on GitHub's servers, `condition` polls another session's `journal.jsonl` — which is a good reason to run it rather than to skip it.

**Honest label on the red: this is a `no-spec` red, the weak kind.** `test/loop/wait-producer-census.test.ts` does not exist, so the command fails for a reason that would be identical for any question written on that path. This pass could not do better: instruments are validated as argv with no shell, so a `-t` name filter against the existing spec file was refused, and the pass may not write code. What partly redeems it is the paragraph above — the builder is not handed "create this file" but a named type, a named missing field, a named data source and a number.

**What a green run does NOT settle.** Only the shape of the corpus. It says nothing about whether a completion-announcing producer is expressible in this harness, whether the operator wants it, or whether the foreign-state cases the parent candidate abandons matter more than the ones it covers. Feasibility answered mechanically leaves desirability, viability and usability exactly where they were.
