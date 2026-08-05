---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[An LLM judge's faithfulness ratings agree with a human's]]

**Candidate solution (unvalidated).** A judge model — independent of the proposer — rates every node on whether it is genuinely grounded in its cited evidence and correctly shaped (opportunity as need, not solution). Produces a per-run faithfulness score without needing hand-built fixtures.

**Approach:** *automated grounding check by a separate model* (proposer ≠ judge).

**Contrast with siblings:** unlike the golden set it needs no curated answers and scales to arbitrary evidence; unlike human sampling it is cheap and continuous but is itself a model whose judgment must be spot-checked.

_Addresses: "Can't tell if the generated tree is actually any good". Also supports "Worry the agent is grading its own homework". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test does the LLM judge agree with human faithfulness ratings" — moved under "An LLM judge's faithfulness ratings agree with a human's" — the belief this test measures now has a node of its own

## Issues
- 2026-07-25 Cross-branch redundancy (2026-07-24 review): same underlying bet as 'Independent judge separate from the proposer' and 'Adversarial grounding judge' — a second pass with no stake reviews nodes against evidence. One build satisfies all three; consolidation candidate.

## Definition of done

"Test does the LLM judge agree with human faithfulness ratings"

```
npx vitest run test/eval/faithfulness-judge.test.ts
```

Green means: the judge emits something a human rating can actually be compared against — a score on a fixed scale, citing the evidence span it scored, stable to within a point across repeat runs. Green does **not** mean it agrees with humans; that needs human ratings to exist as ground truth first, and producing those is a person's work.
