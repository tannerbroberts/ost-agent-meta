---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Usability.** Riskiest assumption: making the key optional (off by default) doesn't confuse setup — users reach a first successful run without thinking they need a key.

**Proposed test (small, fast):** Moderated setup test with ~5 new users; observe whether they complete a first pass without supplying a credential and whether the optional-key path is understood.

**Pre-committed success threshold:** 5 of 5 complete a first run without a key; none blocked or confused about whether a key is required.

_Proposal only — a human runs this with real users. Unvalidated._
