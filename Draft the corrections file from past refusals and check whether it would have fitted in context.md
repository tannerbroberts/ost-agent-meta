---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The deduplicated file is under 2,000 characters, or a stated expiry rule
  brings it under.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the file stays small enough to be read. A corrections file long enough to hold every lesson is one nobody opens, and there is no natural expiry — a refusal that stopped happening because the file worked looks identical to one that stopped mattering.

**Risk category: feasibility.**

**Design.** Build the file retrospectively from every refusal in the harvested transcripts and usage traces, deduplicated by class, with counts. Measure its length. Then apply candidate expiry rules — drop anything not seen in 30 days, keep only the top ten by count — and measure again.

**Why it is small.** The refusals are already captured; this is assembly and counting, with no need for anything to be running.

**What it will not cover.** Size is necessary and not sufficient. A short file may still go unread, and this measures nothing about whether a session that has it actually applies it.
