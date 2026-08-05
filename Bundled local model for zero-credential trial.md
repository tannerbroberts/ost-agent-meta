---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-agent-as-driver.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A small bundled model is good enough for a routine maintenance pass]]

**Candidate solution (unvalidated).** Ship with a small local/bundled model sufficient for routine maintenance passes, so a first-time user can run the tool end-to-end with no external account or network dependency at all.

**Approach:** *remove the external dependency entirely* for the trial path.

**Contrast with siblings:** unlike ambient-agent (depends on the user already having one) and BYO-key (needs an account) this works fully offline, trading some reasoning quality for zero setup.

_Addresses: "Don't want to buy a second AI credential just to try it". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test is a bundled local model good enough for a pass" — moved under "A small bundled model is good enough for a routine maintenance pass" — the belief this test measures now has a node of its own

## Definition of done

"Test is a bundled local model good enough for a pass"

`npx vitest run test/product/offline-trial-pass.test.ts`

The spec asserts the node's actual promise rather than a proxy for it: a full maintenance pass completes with the network disabled and no credential in the environment. Red today because the split is real but lands the other way — the deterministic half (`init`, `status`, `check`, `debt`, `lanes`, `result`) already needs no model and no key, while every reasoning step is supplied by the connected session's model. So the tool is already zero-credential for everything except the part a first-time user would call the product.

**What a green here does not settle, and it is the test's own question.** Whether the bundled model is *good enough*. Completing a pass offline and producing a pass worth having are different claims, and the node concedes the trade openly — "trading some reasoning quality for zero setup". A small local model that maps every evidence item to a vague opportunity and ideates three interchangeable solutions would satisfy this spec completely and would make the trial worse than no trial, because the stranger's first impression would be of the output quality rather than the setup cost. Judging the pass is a person's job.
