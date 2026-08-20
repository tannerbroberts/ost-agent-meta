---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Loading a config that names a repository under adapters.transcript.projectDir
  with product.repos absent must produce one diagnostic naming the missing key
  and suggesting the value. A config with both present, and a config with
  neither, must produce none.
instrument: npx vitest run test/config/declared-path-validation.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Three fixtures: this vault's actual config shape (transcript path present, `product.repos` absent), a fully-configured one, and one configuring neither. Assert exactly one diagnostic, on the first, naming the key and the suggested value. The two silent cases are what stop this from being a check that nags every vault.

**Why it is red today, and on the mechanism rather than the file.** This vault's `ost.config.yaml` was read directly during the 2026-08-06 sweep: `adapters.transcript.projectDir` is `/Users/tanner/dev/OST-Agent` and there is no `product.repos` key anywhere in the file. Config load accepts it silently, and the gap surfaced only when `ost_read_repo` was reached for mid-pass and answered "no product repos configured". A spec asserting a load-time diagnostic fails against today's code because no such diagnostic exists, not merely because the file is new.

**What a green run does not settle.** It proves the shape is detectable. It does not prove the inference is *wanted* — an operator may deliberately harvest transcripts from a directory the agent should not read as a product, and this check would nag them forever. That is a desirability question about a default, answerable only by asking operators, and it is not in scope here. It is also blind to the other half of what closed repo sight on 2026-08-06: `Glob` on the product directory was denied by harness grant, which no config check can see.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/config/declared-path-validation.test.ts` — No test files found, exiting with code 1
- 2026-08-20 **green** (exit 0) `npx vitest run test/config/declared-path-validation.test.ts` — Duration  317ms (transform 38ms, setup 0ms, collect 52ms, tests 9ms, environment 0ms, prepare 35ms)
