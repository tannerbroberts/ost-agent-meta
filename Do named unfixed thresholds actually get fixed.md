---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #desirability #evidence/assertion

**Assumption under test (desirability).** That naming an unfixed threshold causes it
to get fixed — rather than adding 21 more lines to a report and a standing number
that never moves.

**Why it is the riskiest one here.** The census is not in doubt: 21 of 27 tests in
`tetrix-ost` open their pre-commitment with an imperative, and only 4 of 27 carry a
number or an explicit bound. Both were measured mechanically. What is in doubt is that anybody does anything about it.
Fixing a threshold is not typing — it is deciding, before looking, what would make
you abandon an idea you like. That is the single most avoided act in product
discovery, and a list is a weak instrument against it. This tree has a directly
relevant precedent: three paste-ready verdict commands have sat in
`.ost-agent/drafts/` unrun for five briefings, and those took thirty seconds each.

**Proposed test.** Run the census now and record the count per vault. Publish the
named list once — no reminders, no nagging, no second surfacing. Re-run the census
after two weeks.

**Pre-committed threshold:** at least 6 of the 21 `tetrix-ost` tests carry a number
or a bound two weeks later, with no intervening prompt. Fewer than 3 refutes this and
means the report is not the intervention — at which point the honest next move is
"Refuse to record a result against a threshold that was never fixed" or nothing,
**not** a second, louder report.

**What it does NOT test.** Whether the thresholds people then write are any good. A
number written to clear a list is still a number, and this measures only that one
appeared. It also says nothing about `ost-agent-meta`, whose tests are already mostly
bounded — the effect being measured is on the vault that has the problem.

**Lane: compute-only for the census, humans-required for the fixing.** Counting is
mechanical and repeatable and an unattended pass may run it. The two-week wait and
the decision it is waiting for are not something compute can supply, and a pass that
"helps" by writing thresholds itself would be manufacturing the evidence — the agent
must not fix these.

⚠️ Proposed only — the agent does not run tests or record results.
