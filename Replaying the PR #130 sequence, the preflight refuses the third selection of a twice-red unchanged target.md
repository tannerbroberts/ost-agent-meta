---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
threshold: >-
  Given a fixture state directory holding 2 consecutive assertion-red build
  attempts against one target with its node hash unchanged, the target appears
  in the buildable list 0 times out of 1 selection; given 1 attempt, or 2
  attempts with the hash changed, it appears 1 time out of 1
instrument: npx vitest run test/loop/disputed-target-exclusion.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**What the spec asserts.** Construct a loop state directory (the same out-of-vault location `build-pass.sh` uses, `OST_BUILD_STATE`) containing two recorded build attempts against the solution "Ask the open question first, and offer options only once the frame is agreed", each ending with its instrument observed `**red**` on an assertion — not `no-spec`, not a compile failure — and with the node file's hash identical across both. Run the buildable-selection path with that state and assert the target is excluded and named in the report as disputed. Then assert the two negative controls: one attempt does not exclude; two attempts with a changed node hash do not exclude.

**Lane: compute-only.**

**Why it is red today, and what kind of red.** `test/loop/disputed-target-exclusion.test.ts` does not exist — a **no-spec red**, declared as such; it mints no permit until the spec exists and fails on an assertion. The assertion is expected to fail genuinely: the preflight in `examples/automation/build-pass.sh`, read this pass, builds its candidate list from `gate` and `buildable` over the vault and reads no per-target history; the "after 2 attempts" note is produced *after* selection, not consulted before it. The recorded third selection on 2026-08-19 is the observation this spec encodes.

**What a green does NOT settle.** Whether two is the right number, whether a refuted idea and a badly built one deserve the same stand-down, and whether the disputed marker ever reaches discovery in a form it acts on. Feasibility of exclusion only.
