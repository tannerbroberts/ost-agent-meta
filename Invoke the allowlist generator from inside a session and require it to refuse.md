---
type: AssumptionTest
status: unvalidated
source: 'TRANSCRIPT:6e66c934-24d8-4200-b6f2-7af23002c478'
created: '2026-08-06'
evidence: observed
threshold: >-
  All three cases refuse, each with a non-zero exit and zero bytes written to
  the target settings file.
instrument: npx vitest run test/security/allowlist-generator-guard.test.ts
---
#AssumptionTest #unvalidated #evidence/observed

**Lane: compute-only.** Whether a guard refuses is decided by the guard, and the guard is code.

Drive the generator down the path an agent would take to widen its own grant, and require a refusal at each step. Three cases, all fixtures, no network and no real settings file touched:

One — the generator is invoked from a context marked as an agent session rather than a human install. It must exit non-zero and write nothing, and the message must say who may run it.

Two — the skill's `allowed-tools` frontmatter is mutated after install and the generator is re-run in place. It must refuse to widen an existing allowlist without an explicit install-time confirmation, and specifically must not silently add the tool that was appended.

Three — the generator is pointed at a settings file a human has narrowed by hand: the skill declares five tools, the settings grant four, and the omission is deliberate. It must not treat the narrower grant as drift to be repaired. This is the case that distinguishes a generator from a bulldozer, and it is the one most likely to be got wrong, because "the two lists cannot drift" reads as licence to make them equal.

**Pre-committed bar:** all three refuse, each with a non-zero exit and no bytes written to the target settings file. Any one of them writing is enough to kill this candidate outright in favour of "Preflight the run's tool demands against its grant and stop at turn one", which detects the same gap without ever holding the pen.

**What a green run here does not settle.** It proves the dangerous path is closed. It does not prove the solution is wanted: case three passing means the generator tolerates a deliberately narrow grant, which is a mechanism, not evidence that any operator maintains one. It also says nothing about install-time correctness on a real machine — every case here is a fixture, and a generator that behaves perfectly against fixtures can still write to the wrong path on someone's laptop.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/security/allowlist-generator-guard.test.ts` — No test files found, exiting with code 1
- 2026-08-06 **green** (exit 0) `npx vitest run test/security/allowlist-generator-guard.test.ts` — Duration  24.17s (transform 116ms, setup 0ms, collect 93ms, tests 22.80s, environment 0ms, prepare 208ms)
