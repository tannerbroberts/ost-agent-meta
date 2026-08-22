---
type: AssumptionTest
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-22'
evidence: assertion
threshold: >-
  At a 14-day shelf life over this vault's dated measured claims, the expired
  share must land between 10 and 70 percent inclusive. Above 70 the label marks
  nearly everything and discriminates nothing; below 10 it never fires and buys
  nothing. Either side refutes the assumption.
instrument: npx vitest run test/eval/claim-expiry-density.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Pre-committed threshold, both bounds fixed before the count is taken:** extract every dated measured claim in this vault — a section or paragraph carrying a `YYYY-MM-DD` and a figure it asserts — and bucket them by age against a **14-day** shelf life. **The expired share must land between 10% and 70% inclusive.** Above 70% the label marks nearly everything and discriminates nothing, which is this candidate's stated decay mode. Below 10% it never fires, which is the trap the assumption names: a silent label is indistinguishable from a working one. Either side refutes the assumption, and the candidate is closed rather than re-tuned — moving the shelf life until the share lands inside the window would be fitting the parameter to the answer, and this test exists to stop that.

The distribution is reported alongside the share, not just the verdict, because it is the thing a human needs in order to pick a shelf life on purpose rather than by search.

**What the spec asserts.** `test/eval/claim-expiry-density.test.ts` runs the extractor over a frozen snapshot of this vault, computes the share at a 14-day boundary, and asserts both bounds. Frozen rather than live: a test whose subject changes daily cannot be re-run to mean the same thing, and this suite already keeps that discipline in `test/eval/rollup.test.ts`.

**Read the red honestly.** **No-spec red** — the file does not exist, this surface cannot author one, and the command fails today for the same reason any question written on that path would. The bound two-sided threshold is what makes it a working build permit regardless (`src/eval/buildable.ts` keeps a permit on a `no-spec` run when the threshold is bound). The absent mechanism, named from the code: nothing under `src/eval/` extracts dated claims at all — `coverage.ts` scans prose for a pre-commitment lead-in and is the nearest existing reader, and it has no notion of a date or an age.

**What a green does not settle, and this one matters.** That the label would change anybody's behaviour. A well-distributed corpus makes the label *possible*; whether an operator who reads "not measured since 2026-08-16" then goes and re-measures, or shrugs and believes it anyway, is a person's response and no count here reaches it. A green plus an operator who ignores the label is a mechanism that works and does nothing.
