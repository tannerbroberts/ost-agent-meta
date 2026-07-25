---
type: Solution
status: unvalidated
source: >-
  agent-ideation:autonomous-loop-2026-07-25 — generalized from an observed run
  on the tetrix product, where a compute-only verification was converted into a
  committed test rather than into a verdict draft
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Do six cold artefacts show a test beating a verdict draft]]

**The idea.** When a pass runs something in the compute-only lane, its output should default to a **committed test in the product repo**, not a verdict draft in the vault. The draft is still written — a human still records the verdict — but the artefact that survives is executable.

**Where this came from.** On 2026-07-25 a loop was pointed at a tetrix assumption test whose standing briefing described it as a ~15-minute human walk of five journeys against a live database. The loop could have done exactly that: walk the journeys, observe the numbers, write a paste-ready `ost-agent result` line, and hand a human one paragraph to approve. Instead it wrote `visitorFunnelService.pg.test.ts`, which re-runs the same five journeys on every `pnpm test`.

Both routes cost the same compute and produce the same finding today. They differ entirely in what happens tomorrow.

**The claim.** A verdict is a measurement of a moment; a test is a standing assertion. A verification that must be re-run by hand decays silently — the code moves, the finding stays recorded, and nobody can tell that the recorded finding stopped being true. This matters more here than in ordinary engineering, because the whole product's premise is that the map should be *trustworthy over time*. A tree full of results that were true once is exactly the failure mode the believability ladder exists to prevent, arriving through a different door.

**Contrast with siblings under this opportunity.** [[Triage every assumption test by the human-minutes it actually needs, and let compute run the zero-minute lane]] decides *which* tests compute may run — this decides *what compute should leave behind when it runs one*. They compose: lanes without this produce a growing pile of one-shot drafts; this without lanes has nothing to trigger it. The docket sibling compresses the human's residual role and is unaffected either way.

**Where it does not apply, which is most of the tree.** Only a minority of assumption tests have an executable form. "Will an operator hand over real discovery work" cannot become a test file. The rule should therefore be a *default with an escape*, not a requirement — and the escape must not become the path of least resistance, because writing a test is genuinely harder than writing a paragraph and an agent will feel that pull.

**The risk worth naming before anyone builds this.** A test that encodes the wrong threshold is worse than a verdict that encodes the wrong threshold, because it will be re-run forever and its greenness will be read as ongoing confirmation. The 2026-07-25 tetrix run is a live instance: the test it left behind covers the database half of a pre-committed threshold and *not* the browser half, and the pass had to split the node in two to stop a green suite reading as a verified instrument. Whatever this becomes must make that split cheap and obvious rather than depending on an agent noticing.

**Cheapest disconfirmer.** Take three compute-only tests from the existing backlog that plausibly have an executable form. Have compute produce both artefacts for each — a verdict draft and a test — and put the six in front of the operator cold. If the drafts are as useful as the tests, this node is decoration and the lane triage alone is enough.

⚠️ Unvalidated. Proposed by an agent, from a single instance of its own behaviour on another product.
