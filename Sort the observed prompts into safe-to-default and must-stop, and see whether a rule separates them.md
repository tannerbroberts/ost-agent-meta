---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: >-
  The two sorters agree on at least 90%, and a stated rule reproduces the agreed
  sort with no must-stop prompt classified as safe.
instrument: npx vitest run test/runner/no-tty-policy-answer.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that safe-to-default prompts can be distinguished from ones that must stop the run. Some — a destructive overwrite, a force push — should stop no matter what any policy says, and if the line between them cannot be drawn mechanically, the policy is a standing grant with no boundary.

**Risk category: feasibility, with a real ethical dimension** since this is about acting on the operator's behalf.

**Design.** Collect every prompt observed in the transcripts plus the obvious dangerous ones. Have two people independently sort each into safe-to-default or must-stop. Compare. Then attempt to write a rule that reproduces the agreed sort, and check it against the disagreements.

**Why it is small.** A list of perhaps twenty prompts, two sorters, and one attempt at a rule.

**What it will not cover.** A rule that works on known prompts says nothing about an unfamiliar one, and the unfamiliar prompt is where defaulting is most dangerous. Whatever emerges should probably fail closed.

The boundary of this authority is a human's to set. A human runs this and records the result.

## History
- 2026-08-05 instrument: (none) → npx vitest run test/runner/no-tty-policy-answer.test.ts — Asserts the boundary that makes answering-on-the-operator's-behalf acceptable: with no terminal attached a recognised prompt is answered from the written policy and journalled with the question, the answer and the policy line that supplied it, while a prompt outside the policy and any must-stop class — destructive overwrite, force push — stops the run whatever the policy says. Red today because nothing detects the absent terminal or holds a prompt policy.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/runner/no-tty-policy-answer.test.ts` — No test files found, exiting with code 1
