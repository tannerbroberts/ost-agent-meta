---
type: AssumptionTest
status: unvalidated
created: '2026-08-02'
evidence: assertion
threshold: >-
  The check names the missing file and its location in at least three of the
  four reconstructed cases, with no false accusation in a session that is
  correctly configured.
---
#AssumptionTest #feasibility #unvalidated #evidence/assertion

**The assumption under test (feasibility):** that the gap is mechanically diagnosable from inside a session that is missing its tools. The root cause took four passes and a comparison against a sibling vault for a human-driven session to find; the claim is that a check could have named it in under a second.

**How it would run:** reconstruct the conditions of the four scheduled passes that ran without tools and run the proposed check against each. Record what it names.

**The trap this is really probing:** a session with no tools may also lack whatever the check needs in order to run — the tree already carries a separate test, "Check whether a toolless session can even run the tool check", asking exactly that. If that one comes back negative, this candidate cannot fire in the case it was designed for, and the result here is moot regardless of accuracy.

An hour or two, retrospective, no build. Proposed by the agent; a human runs it and records the outcome.
