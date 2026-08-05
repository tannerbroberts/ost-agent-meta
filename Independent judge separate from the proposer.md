---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-dogfooding-idea.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Splitting proposer from judge raises trust more than a proposer's own sign-off]]

**Candidate solution (unvalidated).** Split the roles: the generating agent only proposes; a distinct judge (different model/prompt, no write access to create nodes) checks each node's faithfulness against the cited evidence. The proposer can never sign off on its own output.

**Approach:** *separation of proposer and validator roles*.

**Contrast with siblings:** unlike the tool-enforced no-validate rule (which blocks the agent from a status) this adds an active second opinion; unlike the real-world-signal gate it checks faithfulness, not usefulness.

_Addresses: "Worry the agent is grading its own homework". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test does an independent judge raise trust over self-report" — moved under "Splitting proposer from judge raises trust more than a proposer's own sign-off" — the belief this test measures now has a node of its own

## Issues
- 2026-07-25 Cross-branch redundancy (2026-07-24 review): same underlying bet as 'Independent LLM judge scores faithfulness to evidence' and 'Adversarial grounding judge'. One build satisfies all three; consolidation candidate.

## Definition of done

"Test does an independent judge raise trust over self-report"

```
npx vitest run test/eval/judge-independence.test.ts
```

Green means: the judging call runs under a distinct identity from the proposing call and never sees the proposer's reasoning trace, so the independence this solution is named for is real rather than nominal. Green does **not** mean trust rose — that is a reader's judgement and stays with a human.
