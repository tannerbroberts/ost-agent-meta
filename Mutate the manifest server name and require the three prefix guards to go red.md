---
type: AssumptionTest
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
threshold: >-
  All three known-defective prefix guards go red under a mutation of the
  manifest field they derive from. Three of three, not a majority — a technique
  that catches two of the three known cases has no claim on the unknown ones.
instrument: npx vitest run test/guards/mutation-detects-self-derivation.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** A mutation and a suite run. Nobody is the measurement.

**What it does.** Mutate the server name in the plugin manifest — the shared source the skill generator and the two release tests all derive the tool prefix from. Run each of the three guards against the mutated manifest. Assert each goes red. The guards that stay green are demonstrating the property this opportunity names, and the test that catches them is the technique proving itself against a case with known ground truth.

**Why it is red today.** No mutation harness exists, so there is nothing to invoke. Beyond the missing file, the assertion is about a real, documented, currently-live defect: the three guards exist and are known to have agreed with the bug for 23 releases. That makes this stronger than a bare missing-path red — the mechanism it asserts absent is absent, and the subject it asserts defective is defective.

**A caveat on the path.** This sweep had no repository sight. `ost_read_repo` is off the unattended surface and a direct read of the product source tree was refused for permissions, so the spec path follows this vault's naming conventions rather than the suite as it stands. A human or attended pass should re-point it before treating a green as meaningful.

**What a green does NOT settle.** That mutation testing catches self-derived guards *in general* — this scores it against the three cases that inspired it, which is the friendliest possible sample. It says nothing about cost, nothing about whether the mutation set generalises, and nothing about guards that are missing rather than blind.
