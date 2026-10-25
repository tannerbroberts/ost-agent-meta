---
type: AssumptionTest
source: 'REPO:test/adapters/transcript.test.ts'
created: '2026-10-25'
evidence: assertion
threshold: >-
  exactly 1 reused-id retry and exactly 1 new-call retry counted apart on the
  summary line
instrument: npx vitest run test/adapters/transcript-retry-id-reuse.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.**

**What the spec should assert.** `test/adapters/transcript-retry-id-reuse.test.ts` imports `extractFriction` and `TranscriptSource` from `src/adapters/transcript.ts`, as the existing `test/adapters/transcript.test.ts` does, and reuses that file's fixture shape. The fixture is one session holding three `tool_use` blocks with the same name and input: ids `t1`, `t1`, `t2`. Today that files two retries that look the same. Once built:
- the two retry events carry the reuse fact (`t1` again counts as reused, `t2` as new);
- the rendered body's summary line reads `retry ×2 (1 reused an id already seen, 1 new call)`, in the format the parent solution specifies;
- nothing is dropped, so `events.length` is unchanged. That is the solution's own "nothing is dropped automatically" commitment.

**Pre-committed threshold:** the spec passes. Exactly one reused-id retry and exactly one new-call retry are counted apart on the summary line, and the total event count matches today's.

**Which kind of red this is, honestly: `no-spec`.** The file does not exist, so today's red is the weak kind and grants no build permit. I tried two stronger forms first and the instrument grammar refused both. A `-t` filter on the existing spec was refused for its quotes, and refused again as a non-instrument form without them. The only accepted form is `npx vitest run <path>.test.ts`, and the existing transcript spec passes today. What this node adds over a bare filename is the assertion above and the mechanism that has to change: `extractFriction` keys `seenCalls` on `name:input` alone and never consults `block.id`. Write the fixture first and it goes red on the summary-line assertion against today's code. That is the point at which this test is finished.

**What this does NOT settle.** Whether real transcripts ever contain a same-id repeat (see the parent assumption). And whether a reader discounts the labelled retries, which is the sibling usability test, humans-required on purpose. Green here means the label can be built, not that anyone wants it or that it changes a decision.
