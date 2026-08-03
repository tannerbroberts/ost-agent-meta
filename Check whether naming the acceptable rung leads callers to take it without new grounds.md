---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 5 of 20 retries take the suggested value with no new grounds cited.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a suggestion informs rather than substitutes for judgement. A rung refusal that names the ceiling is one keystroke from a caller declaring the ceiling reflexively — the ladder climbed by autocomplete rather than by evidence.

**Risk category: usability.**

**Design.** Add the suggestion to rung refusals only. Over the following twenty refused calls, record what the caller declared next and whether their retry cited any grounds it had not cited before. A caller that simply takes the named value with no new justification is the failure this is looking for.

**Why it is small.** One message change, and the traces already record every call and its arguments.

**What it will not cover.** Taking the named ceiling is often correct — it may be the honest rung. Distinguishing a reflexive acceptance from a correct one requires reading the justification, which is a judgement, so the count is a flag rather than a verdict.

A human reads the retries and records the result.
