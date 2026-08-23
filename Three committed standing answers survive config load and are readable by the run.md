---
type: AssumptionTest
source: 'REPO:OST-Agent/src/config/schema.ts'
created: '2026-08-23'
evidence: assertion
threshold: >-
  at least 3 of 3 declared standing answers survive loadConfig and are readable
  from the loaded config; today exactly 0 of 3 survive
instrument: npx vitest run test/config/standing-answers.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold:** write an `ost.config.yaml` declaring a standing answer for each of the three prompts this branch's evidence recorded a run stopping on — divergent-branch reconcile, file overwrite, editor — then load it through `loadConfig` and read the three back. **At least 3 of 3 must be readable from the loaded config. Today exactly 0 of 3 are**, because `ConfigSchema` declares no key for any of them and Zod strips undeclared keys rather than rejecting them.

**Why this is red today for a reason specific to this question, and not for a reason every question would produce.** The spec's assertion is not "the file parsed" — a config with all three keys parses cleanly right now, which is the defect. It is that the three values are *present on the loaded object*. A spec that asserted only parse success would be green today and would measure nothing. This one fails on the read-back, and the read-back is exactly the behaviour the solution has to build.

**What a green here does NOT settle.** Only that the answers reach the run. It says nothing about whether the run then honours them at the moment the underlying tool prompts — that is a second, later question about the shim, not this one — and nothing at all about whether pre-answering is the right trade. The solution's own risk paragraph ("a default committed once will eventually apply in a case where it is wrong") is a person's judgement and is untouched by any exit code here.

**Why a new spec path rather than an existing one.** `test/config/` holds eight specs this pass listed; none of them reads a standing-answer key, because no such key exists. Naming an existing green spec would produce a first-run green, which `verifyInstrument` refuses by the red-before-green rule.

_Grounded in a first-party `ost_read_repo` of `src/config/schema.ts` and a listing of `test/config/`. Nothing executed. Rung stays at the `assertion` floor._
