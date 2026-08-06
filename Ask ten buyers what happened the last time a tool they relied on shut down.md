---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  At least 5 of 10 describe a real loss, and at least 3 changed a tool choice
  because of it.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that portability is priced. Most buyers do not value it until they need it, and by then they are not shopping — so this may be a real advantage nobody pays for, which is a different failure from not having one.

**Risk category: desirability.**

**Design.** Ask ten prospective buyers about past behaviour, not preference: has a tool you kept work in ever shut down or been dropped, what did you lose, and what did you do differently afterwards? Only then mention that this tool's output is plain files, and note who connects it to what they just described.

**Why it is small.** Ten conversations, entirely about things that already happened, so the answers are recollection rather than speculation.

**What it will not cover.** Recollection of a past loss predicts stated concern better than it predicts a purchase. Someone burned once may still choose the hosted tool with the better demo.

A human runs this and records the result.

## Issues
- 2026-08-06 Lane unset, and this sweep could not set it. Judged humans-required by the 2026-08-06 unattended pass: the title names an outside party and a recalled past experience ("what happened the last time"), which is story-based interview material and not available to any command. `ost_flag_humans_required` is not granted on the unattended surface, so the judgement is recorded here instead. Left for a human: `ost-agent lane --set humans-required`.
