---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  All 4 of the named per-session findings must be reproducible from rolling
  per-shape records alone, with 0 requiring the original per-session files.
  Fewer than 4 refutes the assumption and the adapter-side candidate is closed
  rather than narrowed.
instrument: npx vitest run test/adapters/rolling-shape-record-fidelity.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold, fixed before the record format is designed:** rebuild this vault's 385 transcript records as rolling per-shape records under the proposed format, then attempt all **4** named findings against those records alone. **All 4 must reproduce, and 0 may need the original per-session files.** Fewer than 4 refutes the assumption and closes this candidate — the format is not to be widened until it passes, because a format widened until it reproduces per-session findings has become per-session storage under another name, which is a different candidate and should be judged as one.

The 4, stated so nobody can pick easier ones after seeing the result: (1) 91 occurrences across 29 sessions; (2) the per-session distribution 9, 8, 7, 6, 6, 6, 5; (3) the single session `90d8aeae` isolated by id at `2026-08-17T07:16Z` with 8 consecutive denials; (4) two byte-identical failing commands 26 hours apart in two distinct sessions.

**What the spec asserts.** `test/adapters/rolling-shape-record-fidelity.test.ts` holds a frozen fixture of transcript records, runs the rolling-record writer over them, and asserts each of the four findings recomputes to the recorded figure from the rolling records only — with the per-session fixture unavailable to the reconstructor, so a reader that quietly falls back cannot pass. It sits beside the existing adapter suite in `test/adapters/`.

**Read the red honestly.** **No-spec red** — the file does not exist and this surface cannot author it, so today the command fails for the same reason any question written on that path would. The bound threshold is what makes it a working build permit regardless (`src/eval/buildable.ts` keeps a permit on a `no-spec` run when the threshold is bound). The absent mechanism, named from the code so the builder is not guessing: `src/adapters/transcript.ts` writes one record per session keyed by session id, and nothing anywhere writes a record keyed by anything else.

**Two of the four are expected to fail, and that is the point.** The assumption's own body reasons that a scalar counter loses findings (2) and (3). This test is written to make that a recorded refutation rather than an argument — the value is in the result being on the tree, not in the outcome being a surprise.

**What this does not settle.** Whether shapes can be identified reliably enough to key records by them, which is a separate belief and the other half of this candidate's risk; and whether a shorter queue is worth anything to the operator, which is nobody's stated preference and no spec's business.
