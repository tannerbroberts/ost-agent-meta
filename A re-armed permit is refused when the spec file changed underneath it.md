---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  Restoring a displaced command re-arms its observation when the spec file's
  contents are unchanged, and refuses to re-arm — leaving the permit un-cleared
  — when the contents differ, even though the command string is byte-identical.
instrument: npx vitest run test/instruments/permit-rearm.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether the identity condition can be made strong enough to be safe. The fixture is built so that the naive implementation fails: two cases with the same command string and different file contents, where one must re-arm and one must not. A candidate that keys on the string alone passes the first and fails the second, and that failure is the finding — it would mean re-arming cannot be done safely without content addressing, which is a much larger change than this node's body claims.

**Why it is red today.** Nothing is preserved across a replacement. The tool un-clears the permit and the displaced command is gone, so there is no re-arm path and no identity condition to test.

**Honest limit on the instrument.** Written without repository sight, so the path is invented and fails first for absence. This one would benefit most from being grounded, because whether content addressing is cheap depends entirely on how permits are currently stored — which this pass could not read.

**What a green here does not settle.** The second failure mode this candidate's body names: that making replacement recoverable makes replacement more frequent. That is a behavioural effect over passes and needs a count, not an exit code.
