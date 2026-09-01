---
type: AssumptionTest
source: 'agent-ideation:2026-08-31-unattended-sweep'
created: '2026-09-01'
evidence: assertion
threshold: zero reserved sections appear in the commentary region across all fixtures
instrument: npx vitest run test/mcp/node-body-claim-split.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Drive `readNodeBody` from `src/mcp/node-body.js` against fixture nodes whose bodies mix an opening claim, several dated `## ` commentary sections, and a reserved block, and assert the three-way split puts each region where it belongs.

**Pre-committed bar:** zero reserved sections appear in the commentary region, across every fixture. This is a zero-tolerance bar rather than a rate because the failure it guards is a human's recorded finding vanishing from the default read, which is the one class of defect this product treats as unrecoverable.

**What the spec asserts, so the builder's job is exactly to make these true.**

- A body of claim paragraphs plus three dated `## 2026-08-31 — …` sections returns the claim paragraphs in `prose` and the three dated sections in a new commentary field, with `prose` no longer containing them.
- The load-bearing case: a fixture whose `## Results` block sits *after* the dated sections still returns that block in `reserved`, and the commentary field contains no reserved heading. Same for `## Uncovered` and `## Instrument Log`.
- The adversarial case: a reserved section whose heading is itself date-prefixed does not get classified as commentary by the date rule.
- A node with no dated sections returns an empty commentary field and a `prose` byte-identical to what `readNodeBody` returns today, so the change cannot alter existing reads.
- `proseChars` and `truncated` report the claim region's true length, not the whole body's — otherwise the cap would still be sized against material the default read no longer serves.

**What this instrument does NOT settle, stated plainly.** It proves the mechanism separates the regions correctly. It proves nothing about whether a reader given only the claim reaches the same decision — that is the fidelity belief beside this one and it needs a person. A green here means the split is safe, not that it is worth making.

**Honest note on this instrument's strength.** `test/mcp/node-body-claim-split.test.ts` does not exist, so today this command fails with no spec found rather than on an assertion. By this repository's own standard that is the weak kind of red: it would fail identically for any question written on that path, so it grants no build permit and this test is not finished until the spec exists and an assertion in it fails. The assertions above are written out in full for that reason — the deliverable is the failing spec, not the filename.

Unvalidated. Agent-proposed 2026-08-31.
