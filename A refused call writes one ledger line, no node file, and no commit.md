---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
threshold: >-
  a refused call adds exactly 1 corrections-ledger line, 0 node files and 0
  commits
instrument: npx vitest run test/mcp/refusal-side-effect-bounds.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility. Small and fast: one refused call against a fixture vault, three counts taken either side of it.**

Build a fixture vault, snapshot three things, then make a call the server must refuse — an `ost_set_instrument` carrying a `-t` filter is the obvious choice, since it is the refusal this branch was created from and is guaranteed to be rejected by `parseInstrument`. Then assert, against that snapshot:

- the corrections ledger under `.git/ost-agent/` gained **exactly one** line, and its `permitted` field names the vitest form;
- the vault gained **zero** node files, and every pre-existing node file is byte-identical to its snapshot;
- `git log` gained **zero** commits.

The third count is the one that would otherwise be assumed rather than checked. Every mutating MCP tool commits with `git add -A`, so a ledger written to the wrong place is swept into a commit rather than staying machine-local, and the failure would look like success from inside the tool.

**Why it is red today.** No refusal path writes anything, so the first assertion fails against current code: the ledger gains zero lines, not one. The second and third assertions pass today and are there to stay green — they are the regression half, pinning the property the candidate must not break rather than the behaviour it must add.

**That mixture is deliberate and is what makes this test worth more than its instrument suggests.** A spec that only asserted the new behaviour would go green the moment someone made a refusal write *anything, anywhere*. Carrying the two must-not-change counts in the same file means the builder's definition of done includes not having broken the inertness of refusals, which is the actual risk.

**Honest labelling of how red it is.** `test/mcp/refusal-side-effect-bounds.test.ts` does not exist, so the first run is filed `no-spec` rather than a true red and would fail identically for any question written on that path. `test/mcp/` is real and populated, and the threshold is a bound count on three specific quantities. The stronger form — naming an assertion inside an existing spec — is not expressible here, because the instrument grammar accepts a bare `npx vitest run <path>.test.ts` and nothing else.

**What a green does not settle.** The noise question this candidate names against itself: whether live recording fills the ledger with a session's own boundary-probing. Three counts around one refused call say nothing about volume across a real pass. And nothing about desirability — no evidence here bears on whether anyone wants refusals recorded at all.
