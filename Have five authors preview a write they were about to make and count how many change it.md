---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At least 3 in 20 previewed writes are altered before confirming.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that seeing the rendered write actually changes what gets written — that the caller composing a call and the caller confirming it are different enough for the confirmation to catch something. If they are not, the preview is pure overhead on every good write.

**Risk category: usability.** Not whether previewing is possible, but whether a preview is read rather than waved through.

**Design.** Over one working week, every mutating call goes through preview first. Record, per call, whether anything was changed between the preview and the write that followed. Do not tell the callers what is being counted, so the measurement is of ordinary behaviour rather than of people being watched.

**Why it is small.** No build is required beyond rendering what would be written and pausing. One week of ordinary work supplies the sample, and the result is a count.

**What it will not cover.** It cannot say whether the changes made were improvements, only that something changed. It also measures the first week, when previewing is novel and attention is highest — a rate that holds in week one may not hold in week ten.
