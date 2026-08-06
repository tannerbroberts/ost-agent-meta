---
type: AssumptionTest
source: 'TRANSCRIPT:1744f10a-e7ce-4e46-a573-a1d99c44960c'
created: '2026-08-06'
evidence: assertion
threshold: >-
  A manifest generated from the tool schemas alone names a rule covering at
  least 60% of the distinct refusal classes in the captured transcript corpus.
  Below 60% the solution's cost claim is refuted, not refined.
instrument: npx vitest run test/preflight/manifest-covers-observed-refusals.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The corpus is already on disk under `.ost-agent/evidence/TRANSCRIPT_*.md` and the schemas are in the repository. Nobody needs to be interviewed to count a coverage ratio.

**What it does.** Classify the distinct refusal messages the transcript channel has captured into refusal classes — read-before-write, response-size cap, tool-not-granted, closed parameter set, malformed body, evidence-rung ceiling. Generate a manifest from the tool schemas alone. Assert the generated manifest names a rule for at least 60% of those classes.

**Why it is red today.** No generator exists, so the spec has nothing to call. That is the weak kind of red and it is worth saying plainly: the pass that wrote this could not read the product repository — `ost_read_repo` is not on the unattended surface and a direct Grep of the source tree was refused for permissions — so the path is named from the vault's own conventions rather than from the suite as it stands. A human or an attended pass should re-point it at the real module before treating a green as meaningful.

**What a green does NOT settle.** Only that a manifest *could* carry the rules. It says nothing about whether a run that receives one composes fewer colliding calls — that is a separate, behavioural claim, and this vault already has a partial instance of the idea (the corrections header in the unattended prompt) that sessions kept hitting refusals around. Desirability, viability and usability are exactly where they were.
