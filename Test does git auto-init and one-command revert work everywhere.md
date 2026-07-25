---
type: AssumptionTest
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
---
#AssumptionTest #ported-from-ost-agent-vault

**Risk category: Feasibility (with potential-harm check).** Riskiest assumption: every agent action maps to a cleanly revertible commit, and git can be auto-instantiated across the environments operators actually use.

**Proposed test (small, fast):** Run a pass in each of: a fresh empty directory, an existing repo, and a machine without git preinstalled; then revert the last N commits.

**Pre-committed success threshold:** git is present/instantiated in all cases and a single revert restores the exact prior state every time.

_Proposal only — a human runs this. Unvalidated._
