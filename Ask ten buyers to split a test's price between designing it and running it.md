---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: The median buyer assigns at least 40% of the fee to design.
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that test design is the valuable half. Since a human runs the test, what is actually sold is design and record-keeping — and if buyers see design as the cheap part and running as the expensive part, they are being asked to pay for the wrong half.

**Risk category: viability.**

**Design.** Describe one concrete assumption test — the belief, the design, the pre-committed threshold, the recorded result with what it failed to cover — and ask ten buyers to split a hypothetical fee between the design and the running. Ask what they would pay for the design alone, given that they supply the running.

**Why it is small.** One worked example and ten conversations, using a test the vault already holds.

**What it will not cover.** A hypothetical split is not a purchase and sits low on the ladder. It would catch the clear failure — buyers assigning almost nothing to design — without establishing a price.

A human runs this and records the result.

## Issues
- 2026-08-06 Lane unset, and this sweep could not set it. The 2026-08-06 unattended pass judged this humans-required — the title names an outside party as the measurement ("Ask ten buyers"), and how a purchaser splits a price between design and execution exists only in a purchaser. It could not record that judgement: `ost_flag_humans_required` is not granted on the unattended surface, so the only permitted outcome for a prose-only test there is `ost_set_instrument`, which would be wrong here. Left for a human: `ost-agent lane "Ask ten buyers to split a test's price between designing it and running it" --set humans-required`.
