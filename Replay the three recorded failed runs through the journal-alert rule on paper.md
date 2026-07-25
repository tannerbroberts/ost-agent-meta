---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (feasibility):** run journals as they exist today carry enough to classify failure without new instrumentation.

**Method:** paper-apply the proposed rule (error field present → failed) to every journal in `.ost-agent/runs/` including the 2026-07-25 auth failure. Minutes, existing data.

**Pre-committed threshold:** 100% of known-failed runs classified failed, zero healthy runs misclassified. Any miss means the journal schema needs a machine-legible status field first.

**Decides:** whether the supervisor lane can build on journals as-is.

*Proposed by the agent — to be run by a human. No results recorded here.*

## The rule this test validated is now the shipped rule — 2026-07-25

The compute-only replay drafted on 2026-07-24 (14 journals: the 1 known failure caught, 0 of 13 healthy runs misclassified) is what `ost-agent` v0.5.0 actually implements — `failed(entry) === Boolean(entry.error)`, in `src/runner/journal.ts`, with the replay's finding cited in the module's own header comment so the next reader can see what the rule rests on.

**This matters for how the verdict gets recorded.** A build now depends on this test's result, and the result is still an unrecorded draft — the paste-ready `ost-agent result` command has been sitting in `.ost-agent/drafts/compute-docket-2026-07-24.md` since 2026-07-24. That is the loop's shape working as designed (compute runs and drafts; only a human records) and also the loop's current bottleneck: three decisive verdicts, one of them a kill, all waiting on about three minutes of reading.

**Nothing here promotes this test.** The agent cannot record its own verdict, and shipping code that assumes a finding does not make the finding true.
