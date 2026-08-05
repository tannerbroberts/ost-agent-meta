---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A ten percent sample estimates whole-tree quality closely enough to act on]]

**Candidate solution (unvalidated).** Periodically sample a handful of generated nodes and have a human rate them against a shared rubric (grounded? need-shaped? useful?), tracking the quality trend over time. Ground truth comes from people, closing the loop the automated methods can't fully close.

**Approach:** *human-in-the-loop quality sampling*.

**Contrast with siblings:** slowest and least scalable, but the only method whose verdict on real-world usefulness is authoritative; ideal as the calibration check on the golden set and the LLM judge.

_Addresses: "Can't tell if the generated tree is actually any good". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked [[Test does a 10 percent sample estimate whole-tree quality]] — moved under [[A ten percent sample estimates whole-tree quality closely enough to act on]] — the belief this test measures now has a node of its own

## Definition of done

[[Test does a 10 percent sample estimate whole-tree quality]]

```
npx vitest run test/cli/review-sample.test.ts
```

Green means: the draw is a real sample — 10% of reviewable nodes, stratified across every layer and bucket rather than the alphabetical head, and reproducible under a seed. Green does **not** mean the sample estimates whole-tree quality; that needs the rubric applied by a person to both the sample and the whole tree, and stays with a human.
