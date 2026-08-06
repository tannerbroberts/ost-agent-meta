---
type: AssumptionTest
source: 'TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab'
created: '2026-08-06'
evidence: assertion
threshold: >-
  The preflight must refuse the recorded collision session and refuse fewer than
  1 in 10 of the sessions that completed with no collision. Either half failing
  kills the candidate: refusing everything means the run never starts, and
  refusing nothing means the guard is decoration.
instrument: npx vitest run test/runner/write-intent-preflight-false-stop.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The working-tree states are reconstructable from this vault's own git history and the captured session records; the preflight rule is a function over them. Nothing here needs a person.

**What the command does.** Replays each captured session's starting repository state through the candidate preflight rule and asserts both halves of the threshold at once — sensitivity against the session where a merge landed mid-run, and specificity against the sessions that finished cleanly.

**Why both halves are in one spec rather than two.** Separated, each is trivially satisfiable by tuning the rule to the other's blind spot, and a builder reading one green in isolation would take it as a result. Pairing them is what makes this falsifiable.

**Why it is red today.** `test/runner/write-intent-preflight-false-stop.test.ts` does not exist, and no preflight rule exists for it to exercise. A missing-file red rather than an assertion red, because repository reads were denied from this surface and no module could be named as the one that would have to change.

**What a green here does NOT settle.** That the rule separates the two cases on the sessions recorded so far — a sample drawn entirely from one operator's machine and this agent's own runs. It says nothing about a busier repository, nothing about whether an operator would leave the guard switched on once it refused them once, and nothing about desirability.
