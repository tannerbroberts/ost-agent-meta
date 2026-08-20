---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
lane: humans-required
threshold: >-
  A recorded yes or no from the operator; a yes must name its conditions (green
  CI, instrument transitioned red→green, squash only, no `## Uncovered` gap) or
  it counts as no
---
#AssumptionTest #unvalidated #evidence/assertion

**The question, asked once and plainly.** "On 2026-08-20 a third build firing found PR #181 already green and merged it by hand into the main checkout rather than standing down. Would you rather the ship step did that on purpose — merge a PR that is green on CI, mergeable, and whose instrument has gone red→green — with nobody watching? If yes, under what conditions?"

**Lane: humans-required.**

**Pre-committed reading of the answer.** A conditional yes supports the assumption and the conditions become the ship step's preflight. A no refutes it and the solution should be set `deferred` with the answer quoted, leaving its two siblings to carry the opportunity. "Not yet" is a no with a date.

**What this does NOT settle.** Nothing about whether the merge mechanism is safe in practice — a yes licenses building it, not trusting it; the first unattended merge is its own observation. And the answer is one operator's, for one trunk; it says nothing about any other team's tolerance.

**Recording.** `ost-agent result "<this title>" -v <supported|refuted|inconclusive> -n "<the operator's words>" -b <who asked> -u "<what the answer left open>"`.

A person outside the building is the measurement here: The operator is irreducibly the measurement: this is a permission over their trunk, and no spec can observe a permission that has not been given.
