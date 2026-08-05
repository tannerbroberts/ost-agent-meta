---
type: Solution
status: unvalidated
evidence: assertion
source: 'INBOX:2026-07-22-efficacy-critique.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test does the golden set discriminate good trees from bad]]

**Candidate solution (unvalidated).** Curate fixtures of real evidence paired with expert-reviewed "good" trees, and score each agent run against them (coverage, faithfulness, no-solution-as-opportunity, etc.). Efficacy becomes a measured regression signal rather than an assumption. Unlike the existing scripted end-to-end test (canned outputs prove only that nodes move), this tests whether the *ideation* is any good.

**Approach:** *benchmark against ground truth*.

**Contrast with siblings:** unlike the LLM judge (scalable, no fixtures) this needs curated data but gives a stable regression baseline; unlike human sampling it runs automatically every build.

_Addresses: "Can't tell if the generated tree is actually any good". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Definition of done

[[Test does the golden set discriminate good trees from bad]]

```
npx vitest run test/eval/golden-set-discrimination.test.ts
```

Red today because there is no golden set and no scorer. `test/eval/` holds judge and planted-instance specs, and nothing in the repository assigns a tree a quality score at all, so there is no number to compare across fixtures. Green means every known-good fixture outscores every deliberately degraded one by a fixed margin — asserted per fixture pair, not on the means, because a harness whose averages separate while individual pairs overlap has discriminated nothing.

Writing this as a spec rather than a sitting is what makes the harness self-checking: a discriminator that stops discriminating after a scoring change goes red on the next commit instead of being rediscovered months later.

What it does not settle: the degraded fixtures are broken in ways their author already imagined. A margin over them is not evidence that the harness recognises a bad tree nobody planted, and it says nothing about whether the score tracks anything a human would call quality.
