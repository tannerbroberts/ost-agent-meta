---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Artifacts are composed incrementally, so there is a line three at which to check]]

**The mechanism: move the check from submission to composition.** The artifact is parsed as it is written rather than when it is handed over, so a dialect violation surfaces at the line that caused it, while three lines exist rather than a hundred and seventy. Nothing about what the surface accepts changes; only when it says so.

**Why this shape.** It targets the actual cost in the evidence, which is not that the artifact was wrong but that it was *long* when it was found to be wrong. A rejection at `(24:12)` and one at `(172:33)` are the same defect and differ by an order of magnitude in what they wasted. Halving the acceptance rate would have saved less than moving either of those checks earlier.

**Compared to its siblings.** The only candidate that helps a composer who does not read documentation and does not start from a template — it needs no cooperation at all, which given that the observed failure is a confident habit rather than a knowledge gap is the most valuable property on offer. It is also the most expensive: it needs the surface to expose a parse-only entry point, and it needs the composer to call it midway through work it currently does in one shot, which is a change to how composing happens rather than a change to a message.

**What would make this the wrong pick.** If artifacts are genuinely composed atomically — written whole in a single act with no intermediate state to validate — then there is no "line three" at which to check, and this reduces to a dry-run before submission, which is a smaller and different idea. Worth settling that before building: whether the composer *can* check midway is a question about the composing surface, not about the target one.

⚠️ Unvalidated. Agent-ideated on 2026-08-05.

## Definition of done

[[Check a partial artifact is rejected at the offending line rather than at submission]]

`npx vitest run test/eval/incremental-parse.test.ts`

A three-line fragment containing a type annotation is rejected at its own line, and incompleteness is not itself an error — that second clause is the one that decides whether this node is buildable, since a parser which only accepts whole input has nothing to offer a partial artifact. Red today because parsing happens at submission and nowhere else.

## History
- 2026-08-05 unlinked [[Check a partial artifact is rejected at the offending line rather than at submission]] — moved under [[Artifacts are composed incrementally, so there is a line three at which to check]] — the belief this test measures now has a node of its own
