---
type: Assumption
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-28'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**The belief, stated so it could be false:** every entry that reaches the standing queue carries a real `askedAt`, no matter which surface put it there — a mid-pass flag, a human's CLI classification, or a test created humans-required in the first place.

**Why it is the load-bearing belief under this solution.** The parent node's own argument is that age is what separates a queue from a second inbox: "An ask that has been outstanding for eleven days is a different object from one filed an hour ago, and only the queue can tell the operator that." If an entry can arrive with no date, the queue degrades into exactly the undated backlog the node says it is not — and it does so silently, because a null age still renders as a row.

**Why this pass thinks it is currently false, from first-party repository reading (2026-08-28).** Membership and age come from two different places. `src/ost/pending-asks.ts` admits an entry when *either* the test's lane says a person is what it waits on *or* an ask is on the ledger — but `askedAt` and `ageDays` are read from the ledger alone, and are `null` when there is none. `src/ost/lanes.ts` calls `appendAsk` from the lane-setting path. So a test that acquires the humans-required lane at creation, rather than by being flagged or classified later, enters the queue through the lane branch and never touches the ledger.

The production reading matches: this pass's own `ost_next_work` reports 52 outstanding asks and says all 52 "predate ask tracking and have no recorded age." Not most — every one. A partial legacy migration would leave a mixture; a creation path that never files leaves exactly this. One entry, "A human re-judges the first twelve extent flags against Torres's test", is a test this vault's own sweeps created with `humansRequired` supplied at creation, and it carries `lane: humans-required` with `askedAt: null`.

**The consequence worth naming.** The one surface that creates humans-required tests in volume — an unattended pass calling `ost_create_node` — is also the surface on which `ost_flag_humans_required` is withheld. So the path that files asks is closed to the actor that generates them, and the path that is open to it does not file. That is why the count is 52 of 52 rather than a few stragglers.

**What would make this belief true after all, and would refute the reading above:** creation could file an ask somewhere this pass did not read (`src/mcp/server.ts` was not opened), or the 52 could genuinely all predate the ledger. Either would show up as a green on the test beneath this node.

**Class:** feasibility. It is a question about what this codebase does, answerable by a spec rather than by anyone's afternoon — which is why it is instrumented rather than sent to the humans-required lane.

_Source: first-party `ost_read_repo` reads this pass of `src/ost/pending-asks.ts`, `src/ost/lanes.ts`, `test/ost/pending-ask-queue.test.ts` and `test/mcp/lane-consumer.test.ts`, plus this pass's own `ost_next_work` response. Observed behaviour of the product; grounds feasibility, not demand. No test was run and no result is recorded._
