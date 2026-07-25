---
type: Solution
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Run the compute-only backlog today and count decisive verdict drafts]]

**The idea.** Classify each test at birth (and the 66-test backlog now) into three lanes: COMPUTE-ONLY (replays, audits, paper-classifications over existing data — no customer, no fabrication risk), ONE-COMMAND (compute prepares the full verdict draft; the human's entire role is reading one paragraph and running one pre-filled `ost-agent result` line), and HUMANS-REQUIRED (real outside people irreducibly in the loop). The ambient agent then runs the compute-only lane unprompted and keeps the one-command lane's drafts current.

**Contrast with siblings:** this makes the existing backlog self-serving; the docket sibling compresses the human's residual role; the paging sibling inverts who initiates. The proposer/disposer boundary is preserved exactly: compute runs and drafts, only the human records — `ost-agent result` stays human-only.

**Trade-off:** lane classification is itself a judgment; a mislabeled humans-required test run by compute would fabricate evidence. The lane label must be conservative and auditable.

## Build note — 2026-07-25 (autonomous bootstrap loop; feasibility evidence, NOT validation)

**Shipped as `ost-agent` v0.6.0** (commit `7f8de06`). This does not move the node's status: building a thing is not evidence that anyone needs it, and the operator who described the constraint has not used it yet.

**What was built, against the shape this node proposed.** A `lane` field on every `AssumptionTest`, in frontmatter beside the rung; `ost-agent lanes` to see the tree grouped by what each test costs; `ost-agent lane "<test>" --set --by --why` to classify one, attributed and recorded in the node's History so any label can be traced back to who made the call. 31 new tests, 243 green across 42 files, `tsc --noEmit` clean.

**The trade-off this node named — "a mislabeled humans-required test run by compute would fabricate evidence" — was answered structurally rather than with care.** Three separate mechanisms, because the failure is unsurvivable and care is not a mechanism:

1. **The vocabulary fails closed.** Exactly one lane (`compute-only`) is runnable by an unattended pass, and *everything else answers no* — an unclassified test, a lane a future version invents, a typo, an empty string. Unclassified never means "safe to automate". This is the believability ladder's floor rule applied to a second axis, and it is enforced by test: if a second lane ever becomes compute-runnable, that test fails and someone has to argue for it.
2. **A garbage lane is dropped at deserialization**, not carried into memory and trusted downstream.
3. **The triage aid can only ever raise a hand.** `suggestCaution` scans a test for phrases naming people outside the building and quotes the one that matched (`names an outside person: "interview"`). It never returns a lane compute may run, and its silence means "no marker found", never "safe". The permissive call is a human's by construction — a helper that could talk a pass into running a test would defeat the point of having lanes at all.

**A fourth lane was added that this node did not propose: `pending-permission`.** Folded in from the observed stall recorded on the parent opportunity — `npm publish` is blocked by a credential, not a judgement. Filing it as a decision would make a decision docket feel like chores, which is how dockets die. This is the tree feeding the product directly: an opportunity note from one pass became a type in the next pass's code.

**What was deliberately NOT built, and why it is the interesting half.** This node's second clause — *"the ambient agent then runs the compute-only lane unprompted"* — is not implemented. Only the classification model, the report, and the setter are. The gap is not laziness; it is an unanswered question the agent should not answer alone: **who may set a lane?** If the agent can label a test `compute-only`, then the agent can authorize itself to run it, and all three mechanisms above become decoration. The lane surface is therefore CLI-only for now, exactly as `ost-agent result` is. Exposing it over MCP is a human's call and is named as such in the standing briefing.

⚠️ Still unvalidated. Built, not wanted-by-anyone-yet.
