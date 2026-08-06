---
type: AssumptionTest
source: 'agent-ideation:2026-08-06-unattended-sweep'
created: '2026-08-06'
evidence: assertion
threshold: >-
  Every stored probe completes in under 5 seconds and its output still equals
  the literal recorded beside it. A probe too slow or too environment-dependent
  to re-run in CI fails, and its literal must be marked as trusted-not-verified
  rather than left looking checked.
instrument: npx vitest run test/guards/stored-probes-still-agree.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** Running commands and comparing strings.

**What it does.** Collect every guard carrying a recorded literal with a stored probe. Re-run each probe. Assert the output matches the literal, and assert the whole set completes fast enough to belong in CI. Failures split two ways and the distinction is the finding: a literal that has drifted is a caught staleness, while a probe that cannot run unattended is a recording nothing can ever re-verify.

**Why it is red today.** The convention does not exist — there is one recorded literal with a probe above it, added as the fix for the prefix defect, and no machinery that collects or replays them. Mechanism-missing rather than merely file-missing, though the path itself is named from vault convention because this sweep had no repository sight.

**What a green does NOT settle.** Only that the recordings are current. It does not establish that recording beats deriving in general, that the boundary between external and internal contracts is drawn correctly, or that the practice survives contact with a contributor who would rather update the literal than investigate the drift — which is the golden-file failure mode the parent solution names and this test cannot see.
