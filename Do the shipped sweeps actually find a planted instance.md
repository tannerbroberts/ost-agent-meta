---
type: AssumptionTest
created: '2026-07-27'
evidence: assertion
---
#AssumptionTest #evidence/assertion

**The single assumption.** That the sweeps and checks this project has already shipped would each find an instance deliberately planted in their subject — i.e. that they are actually looking at what they claim to be looking at.

**Why it is worth checking rather than assuming.** Three of this codebase's reporting rules have been found blind AFTER shipping green: the lane reader (fragment read as declaration), the eleven audio tests that could not fail, and now the history sweep. In every case the rule reported success while covering less than it claimed. The common property is that none had ever been observed finding anything.

**Proposed test.** For each shipped check — `ost-agent check`'s invariants, the lane-conflict rule, the debt/threshold scan — plant one synthetic violation in a scratch copy of a vault and confirm the check reports it. Record which checks pass this and which do not.

**Lane: compute-only.** Scratch copies of two local vaults and the CLI. Nothing written to either real tree, no credential, no outside person.

**Pre-committed threshold, fixed before the test runs.** If **2 or more** shipped checks fail to find their planted instance, blindness is the codebase's default rather than an accident, and [[Seed every sweep with a known-present instance it must find]] becomes the primary fix rather than a nice-to-have. **0 or 1** means the existing verify-failing-first discipline is mostly working and the positive control is a belt-and-braces addition that can wait. The count is of CHECKS, not of planted instances, so a single check missing three plants counts once.

**What this cannot tell anyone.** Nothing about a check that finds its planted instance and still misses real ones for an unrelated reason — a plant is by construction the shape its author already imagined.

⚠️ Proposed only — the agent does not run tests or record results.
