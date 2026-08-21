---
type: Solution
status: unvalidated
source: 'agent-ideation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A clear the scanner states in its own issue text is one a pass will quote rather than paraphrase]]

**Mechanism.** The issue string `scanExtentOverlap` emits today ends with two dispositions — "merge with ost_merge_nodes, or rewrite each from its own evidence and say what separates them". Add the third one the code already honours: "or, if a solution could address one and not the other, `ost_annotate` this node with this exact text to record the pair as distinct". Nothing else changes: the key stays the whole issue string, so a clear still expires the moment either sibling's extent changes (the record counts are part of the string), and the matching code in `detectHygiene` is untouched.

**Variation dimension: who-does-the-work — the scanner, not the pass.** Today the pass does two jobs: judge the pair, and guess the key that records the judgement. This candidate moves the second job to the scanner, which is the only party that knows the key, and leaves the pass only the judging. Nobody new is involved and no step is removed.

**Against its siblings.** "The scanner matches a prior annotation by rule and sibling, not by whole string" changes the key so prose verdicts count; this keeps the key and discloses it. "Extent verdicts go through the typed suppression ledger" moves the clear off the agent surface onto a human's CLI; this keeps the clear exactly where the code put it. It is the cheapest of the three — one string — and the one that leaves the agent able to silence a flag with a sentence, which is the risk the third sibling exists to remove.

**What it deliberately gives up.** Any verdict written before the text changed still does not match; the twelve cleared on 2026-08-21 were cleared by hand. And a pass that reads the instruction and still paraphrases is not helped — the belief this rests on is that disclosure is what was missing, not discipline.

⚠️ Unvalidated. Agent-ideated.

## Definition of done

"Every extent issue string names ost_annotate with its own text as a disposition, and annotating with that full string still clears the flag"

`npx vitest run test/ost/extent-issue-names-clear.test.ts`

No-spec red as of 2026-08-21: the file does not exist, so the command fails on "No test files found" and grants no permit until a builder writes the spec named on the test node — whose first assertion (`toContain("ost_annotate")` on each of the three issue strings) then fails against today's `src/ost/extent.ts` for a reason specific to this solution.
