---
type: Solution
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
killIf: >-
  Any harvested session is found where two distinct calls share one tool_use id,
  or where the change drops a retry that the raw file shows was a separate call
killBy: '2027-04-17'
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Keying on the call id removes the double-count and still files a repeat made under a new id]]

**Variation dimension: bought-vs-built. Position taken: adopt the host's own call identifier unchanged, and build nothing that guesses which lines are real.**

Every `tool_use` block already carries an id the host and the API assign: `toolu_…`, unique per call. This candidate makes that id the only thing that says whether two blocks are the same call. A block whose id has already been seen is the same call written again and is skipped entirely. A retry is only filed when a **new** id carries a `name` and `input` matching an earlier call. Today's `${name}:${input}` signature stays, but only to compare calls that are already known to be different.

**How it differs from the sibling that filters entry types.** That sibling builds and maintains a list of which line types are turns. It is right only while the host's line types stay as they are today. This candidate does not care where a copy appears or how many copies there are. Whatever the host writes, one id is one call. The dependency is moved from this product's knowledge of the host's file layout to the host's guarantee that ids are unique. That guarantee is narrower and is the host's own contract.

**What it deliberately gives up.** It still scans the blob lines. Anything else wrong with them, such as a copied `tool_result` with `is_error: true`, still gets through unless the error path is keyed on `tool_use_id` too. That would be the same idea applied once more, and a builder should check it. It also needs the spec's fixture helper changed: `assistantTool` in `test/adapters/transcript.test.ts` gives every call the id `"t1"`. So the existing test "reports a repeated identical tool call as a retry" would go red under this change for a reason that has nothing to do with the bug.

**Honest note on how this was ideated.** All three candidates under this opportunity were written in one context by one author, one after another. This surface cannot run independent blind ideators, so discount their apparent distinctness. This one and the entry-type filter both fix the code at read time, and they differ mainly in what each trusts about the host.

Unvalidated. Agent-ideated 2026-10-17; for a human to review.
