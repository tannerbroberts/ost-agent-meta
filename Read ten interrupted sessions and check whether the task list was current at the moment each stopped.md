---
type: AssumptionTest
created: '2026-10-01'
evidence: assertion
lane: humans-required
threshold: >-
  at least 7 of 10 interrupted sessions show the item being worked marked
  in-progress at the stop
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Usability test of one belief:** that an agent keeps marking items in-progress and done throughout a run, instead of writing the list after the fact at a clean end that a backgrounded session never reaches.

**Method.** Pick ten sessions from the transcript channel that ended without a clean close. These are backgrounded, interrupted or timed-out sessions, chosen before anyone looks at their task lists. For each one, find the last tool call before the stop. Then check whether the task list at that moment had that step marked in-progress, or at least had the steps before it marked done.

**Pre-committed threshold:** at least 7 of 10 show the item being worked marked in-progress at the stop. Fewer than 7 refutes the belief. In that case the parent solution narrows the gap this opportunity describes but does not close it, as its own prose already warns.

**What this does not settle.** It says nothing about whether the next pass trusts the list or is misled when the list is stale. That is the sibling assumption, and it already has its own test. Ten sessions from this vault's own unattended firings are one actor, so the result grounds usability for this harness, not for agents generally.

Proposed by the 2026-09-30 unattended sweep. A human runs it and records the result with `ost-agent result`.

A person outside the building is the measurement here: A person has to read the transcripts of ten backgrounded or interrupted sessions against their task-list state. The artefact is the harness's own task list, not code in product.repos, so no spec in this repository can observe it.
