---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: Both reproduced commands fail promptly rather than prompting or hanging.
instrument: npx vitest run test/runner/non-interactive-honoured.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that invoked tools honour the convention. The ones that ignore it are exactly the ones that caused the problem — a git that prompts for a reconcile strategy despite a non-interactive environment will hang as before, and the run will now believe it cannot.

**Risk category: feasibility.**

**Design.** Take the specific commands that stalled in the harvested transcripts: the git that hit divergent branches, the copy that asked to overwrite. Set every non-interactive signal available — the environment variables, the flags, the config — and reproduce each situation. Record whether the command fails promptly, prompts anyway, or hangs.

**Why it is small.** The failing commands are already named in the evidence, and reproducing each is a couple of minutes.

**What it will not cover.** Two commands are not the whole tool chain, and a tool added later brings its own behaviour. What this establishes is whether the convention works for the failures actually observed.

## History
- 2026-08-04 instrument: (none) → npx vitest run test/runner/non-interactive-honoured.test.ts — Reproduces the two situations named in the harvested transcripts — the git that hit divergent branches, the copy that asked to overwrite — under every non-interactive signal available, and asserts each fails promptly rather than prompting or hanging, which is the node's whole threshold. It fails today because nothing sets those signals and no harness reproduces either command.
