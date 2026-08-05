---
type: AssumptionTest
source: 'agent-ideation:2026-08-05-unattended-pass'
created: '2026-08-05'
evidence: assertion
threshold: >-
  With the MCP surface removed, the fallback resolves the same vault the MCP
  surface would have and produces byte-identical ingest / check / status / debt
  output; every write verb is refused rather than routed; and a fallback run is
  not able to emit a report that a clean-run reader would accept.
instrument: npx vitest run test/loop/mcp-absent-fallback.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: feasibility, with the potential-harm edge the parent names.**

**The assumption under test.** The parent states its own distinguishing assumption in one sentence: *"that the CLI path can actually reach the same vault the MCP surface would have. If the tools are missing because the whole install is wrong, the fallback is missing too."* That is the whole candidate. If it is false, every other argument about degraded runs is moot, and it is settled by running the fallback against a fixture vault with the MCP surface removed — not by asking anyone anything.

**Why the threshold has three clauses and not one.** Reaching the vault is necessary and nowhere near sufficient.

1. *Same vault, same answers.* Byte-identical read-only output is the strong form. A fallback that resolves a different vault, or the right vault by a different route that quietly reports different counts, is worse than no fallback, because the degraded run then enters the record as a clean one carrying wrong numbers.
2. *The write half is refused, not routed.* This is the parent's own "sharpest version" — fall back for ingest / check / status / debt, refuse authoring — and it is the clause that keeps the risk asymmetry pointing the safe way. Untested, it is a paragraph; tested, it is a guard.
3. *A fallback run cannot pass as clean.* The parent is explicit that this candidate is only safe if it depends on [[A degraded pass has its own name and is not allowed to report a clean run]] rather than standing beside it. Asserting the dependency mechanically is what stops the two being shipped separately, which is the sequence that produces [[A failed pass reports success, so my automation can't tell]] through the front door.

**What is red today.** There is no fallback path, so clauses 1 and 2 fail on a missing mechanism. Clause 3 is the interesting red: it fails against a mechanism that *does* exist, because nothing today distinguishes a report produced without the MCP surface from one produced with it. That third assertion would go red against a naive implementation of the first two, which is the point of writing all three in one spec.

**What a green result does NOT settle.** Whether a human reading the degraded report notices. That is [[Show readers a degraded run report and see whether they notice]], whose own text says the measurement *is* what a person notices and that constructing a mechanical proxy would answer a different question. This test deliberately does not construct one: clause 3 asserts the report is *marked*, never that anyone reads the mark. A green here plus an unrun sibling means the fallback is mechanically safe and its safety is still unobserved.

**Lane: compute-only.** A fixture vault and an environment with the MCP surface withheld; no person is the measurement.

⚠️ Unvalidated. Agent-ideated by an unattended pass from the parent's own stated distinguishing assumption. Nothing here was run.
