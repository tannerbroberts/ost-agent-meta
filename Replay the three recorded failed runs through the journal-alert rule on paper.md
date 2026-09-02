---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-25-friction-a-pass-that-dies-on-a-driver-error-still-exits-0.md'
created: '2026-07-25'
evidence: assertion
authorship: machine
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

## Issues
- 2026-08-05 Deliberately NOT instrumented by the 2026-08-05 unattended pass, and the reason is the finding. This test's rule is already shipped: the node's own body records that `ost-agent` v0.5.0 implements `failed(entry) === Boolean(entry.error)` in `src/runner/journal.ts`, with the replay's finding cited in that module's header comment. A spec written against it now would pass on the day it was written, and an instrument that cannot fail measures nothing and hands a builder no definition of done — so setting one here would have made the backlog look one item shorter while adding nothing. The real outstanding work is not an instrument, it is a recording: the compute-only replay (14 journals — the 1 known failure caught, 0 of 13 healthy runs misclassified) has been sitting as an unrecorded draft with a paste-ready `ost-agent result` command in `.ost-agent/drafts/compute-docket-2026-07-24.md` since 2026-07-24. That is roughly ten days of a decisive verdict waiting on a few minutes of human reading, while code that assumes the finding is already in production. Worth stating plainly for whoever triages next: shipping code that depends on a result does not make the result recorded, and this node is the clearest instance in the vault of the gap between the two. Two sibling verdicts are named in the same docket file and are presumably in the same state.

## 2026-09-01 unattended sweep — this node was listed as unexamined, and its own 2026-08-05 note had already resolved it

Three lines, and the point is about the census rather than about this test.

**This node appears in the residue of eight "genuinely unexamined" tests** enumerated on "The biggest queue on my report is one the surface reading it to me has no tool to clear". It is not unexamined: the Issues bullet above, dated 2026-08-05, resolves it in full — the rule is already shipped in `src/runner/journal.ts`, so a spec written against it would be green on the day it was written and the write boundary would refuse it as already-built rather than record it.

**Why the census could not see that.** The enumeration matches the frontmatter block whole and excludes any file carrying `instrument:` or `lane:`. Resolving a test as non-instrumentable leaves no frontmatter trace at all — the finding lives in prose — so a correctly-examined test is indistinguishable from an untouched one. That makes the census's unexamined figure an upper bound rather than a count, which is now recorded on the census node itself.

**The outstanding work here is still a recording, not an instrument.** The compute-only replay (14 journals: the 1 known failure caught, 0 of 13 healthy runs misclassified) has a paste-ready `ost-agent result` command sitting in `.ost-agent/drafts/compute-docket-2026-07-24.md` since 2026-07-24, with two sibling verdicts in the same docket. Recording a result is a human's `ost-agent result`, so this surface can only point at it again.

_Nothing was executed, no instrument set, no rung moved, no status changed. Read first-party from disk during the 2026-09-01 unattended sweep._
