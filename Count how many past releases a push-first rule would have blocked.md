---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
instrument: npx vitest run test/release/push-first-blocked-census.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.** Whether the rule's cost lands on the party that can least afford it.

**The assumption under test.** That refusing to release from unpushed history blocks mostly bad releases and few good ones. The candidate carries a specific worry: because push and publish are both gated by the credential in "Every run ends blocked on a credential only I hold", a strict push-first rule makes the credential holder mandatory for every release — on a project whose stated constraint is "I need the tree's output to be actionable by compute alone, because my hours don't exist". If the rule mostly blocks releases that were fine, it converts an occasional coordination problem into a permanent human dependency.

**The test (replay, no build, no publish).** For every release in the project's history, reconstruct from git whether the releasing tree was ahead of, behind, or diverged from `origin/main` at the moment of release. Classify each: **would have been allowed**, or **would have been refused**. Then a human judges each refusal against one question: **was this release actually problematic, or was it fine and merely unpushed?**

**Pre-committed threshold.** Of the releases the rule would have refused, **at least 50% must be judged genuinely problematic**. Below 50%, the rule blocks more good releases than bad ones and the candidate is closed in favour of its registry-checking sibling, which allows the divergence and fixes only the number.

**The second number, which matters as much as the threshold.** Total refusals as a share of all releases. Even at a perfect 100% precision, a rule that stops one release in two makes the credential holder a participant in half of all releases, and that is the trade the operator is actually being asked to accept. A result that reports precision without reporting frequency has not answered the question this test was written for.

**And the motivating case, checked explicitly.** Would the rule have prevented the 2026-07-26 near-collision? The builder's work was two commits ahead of origin and unpublished, so on the face of it yes — but confirm rather than assume, because the loop's release came from a different tree that may itself have been in sync, in which case the rule constrains only one of the two trains and the collision survives it.

**Who runs it.** A human, from git history. Nothing is published.

## Issues
- 2026-08-05 2026-08-05 (unattended sweep) Left un-instrumented on purpose, and the reason is worth recording rather than leaving as silence. This test's threshold splits across two lanes and only one of them is mechanical. Reconstructing from git whether each releasing tree was ahead of, behind, or diverged from `origin/main` at the moment of release — and therefore which releases the rule would have refused, and the refusal rate as a share of all releases — is a computation over history already on disk, settleable by a spec today. The pre-committed bar is not that: "at least 50% must be judged genuinely problematic" turns on a person reading each refused release and deciding whether it was actually a problem or merely unpushed, and no exit code produces that judgement. Attaching a single command here would have gone green on the arithmetic while the clause the candidate actually lives or dies on stayed untouched, which is the failure mode the ruleset warns about — a passing test read as a validated solution. For a human: this splits cleanly into a replay test (instrumentable now: refusal set and refusal frequency, both mechanical) and a judgement test (humans-required: were the refused releases problematic). The node itself already says the frequency number "matters as much as the threshold" and that a result reporting precision without frequency has not answered the question — so the mechanical half is not a consolation prize, it is half the deliverable. Creating the split node is outside this sweep's scope and `ost_flag_humans_required` is not granted on this surface, so neither half could be filed correctly from here.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/release/push-first-blocked-census.test.ts — Replays every past release in this repository's history against the proposed precondition — working tree ahead of, behind, or diverged from `origin/main` — and counts how many would have been refused, which is the adoptability figure this test pre-commits to. It fails today because the release path has no ahead/behind precondition at all: there is no `git rev-list --left-right --count` gate to call, and nothing replays historical releases against one, so the census has no subject.

## Instrument Log
- 2026-08-05 **red** (exit 1) `npx vitest run test/release/push-first-blocked-census.test.ts` — No test files found, exiting with code 1
