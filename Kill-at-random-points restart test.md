---
type: AssumptionTest
status: unvalidated
source: 'agent:P4_assumptions'
created: '2026-07-24'
---
#AssumptionTest #unvalidated #feasibility

**Assumption under test (feasibility):** A pass can be killed at any instant and restarted with no corruption, no duplicate nodes, no half-written state, and no stuck locks.

**Proposed test:** Run a pass against a scratch copy of the vault and kill the process at twenty randomly chosen points. After each kill, restart and let it finish. Check the resulting vault for validity, duplicated nodes, truncated files, and orphaned locks.

**Size:** a scripted afternoon against a throwaway vault — never the live one.

**Pre-committed threshold:** 20 of 20 restarts produce a valid vault with zero duplicates and zero partial nodes, and the pass completes. Idempotence is not a percentage; a single failure means the guarantee does not exist.

**Decides:** whether "kill it whenever you like" can be promised to stakeholders, which is the load-bearing claim of the parent opportunity.

Proposed by the agent — to be run by a human against a scratch vault. No results recorded here.
