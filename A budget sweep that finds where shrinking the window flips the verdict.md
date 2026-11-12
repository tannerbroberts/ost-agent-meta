---
type: Solution
source: 'INBOX:2026-08-11-founder-vision-restatement.md'
created: '2026-08-11'
evidence: assertion
authorship: machine
---
#Solution #compression #unvalidated #evidence/assertion
[[Recorded decisions exist in enough volume for a sweep to find a knee rather than noise]]

Every window size in the product today (280-char excerpts, list caps of 25, byte budgets) is a number somebody picked. This solution replays recorded decision surfaces — evidence records against their mapping decisions, tree states against their rollup verdicts — at progressively smaller budgets and reports where the verdict flips: the knee of the fidelity curve. Window sizes stop being guesses and become measurements with a stated margin, and a change that moves the knee is caught by an instrument instead of by an operator noticing degraded passes.

## Definition of done

"Sweep recorded decisions at shrinking budgets and require a measurable knee for at least one surface"

`npx vitest run test/compression/budget-knee.test.ts`

**What the spec has to assert (from the test's own threshold).** For at least one real surface, replaying recorded decisions down a ladder of byte budgets gives a verdict-flip rate under 1% at the full budget and over 5% below some budget. A curve that is flat across the measured range fails it.

**State of the command on 2026-11-12.** The spec file does not exist: `test/compression/` in the product repository holds only `fidelity-contract.test.ts` (listed this firing). A run today files as `no-spec`, which is not a red about this question. The builder's first deliverable is the spec failing on the knee assertion.

**What a green does not settle.** That a knee exists in this vault's recorded decisions, which are mostly transcript-friction records of similar shape. It says nothing about another vault, or about whether an operator would change a window size because of the number.

The test title is quoted, not linked: its one backlink belongs to its parent assumption. Added by the 2026-11-12 unattended sweep; nothing was executed.
