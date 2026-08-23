---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A helper rewritten against the bundled runtime stays short enough that the operator would still edit it]]

Stop writing helpers in whatever the machine happens to provide. Write them against a runtime the project already depends on and ships — the same one the rest of the tool runs on — so the version is a property of the project rather than of the operating system. The machine's shell becomes irrelevant.

The project already does this for its main surface, which is bundled and runs on a known runtime. Helper scripts are the one place where a dependency on the host's decade-old bash crept back in.

**Compared to the alternatives.** Removes the entire class permanently, across every machine, rather than guarding one boundary of it — no manifest to maintain, no floor to guess, no linter to keep configured. It costs more to write each helper, since a shell one-liner becomes a small program, and it makes helpers heavier for tasks where shell genuinely was the right tool.

**What would make this the wrong pick.** Some helpers exist precisely because they are five lines of shell that anyone can read and edit. Rewriting those against a runtime makes them longer, less transparent, and harder for the operator to change — which may cost more than the compatibility is worth.

## History
- 2026-08-05 unlinked "Rewrite the shortest helper against the bundled runtime and compare length and readability" — moved under "A helper rewritten against the bundled runtime stays short enough that the operator would still edit it" — the belief this test measures now has a node of its own

## Issues
- 2026-08-23 2026-08-23 unattended sweep, repo sight held: checked whether the missing instrument here is an oversight, and it is not. The mechanical half of this candidate — how many shipped helpers genuinely need a shell — is already owned by a sibling's test, "Take the harvested commands and count how many genuinely need a shell to do their work", and its harvester exists in the repo (`scripts/harvest-shell-necessity-corpus.ts`). Writing a second spec here would measure the same fact under a second name. What is left beneath this node is the one belief the harvest cannot answer: "A helper rewritten against the bundled runtime stays short enough that the operator would still edit it" — a readability judgement about a person, which no exit code settles. Repo facts backing this, read first-party: `scripts/` is already entirely TypeScript, and the shell surface is exactly two files, `examples/automation/autonomous-pass.sh` and `build-pass.sh`. So the rewrite this candidate proposes is small and already mostly done, which sharpens the remaining question from "is it feasible" to "is the rewritten version still one the operator would open and change." Deliberately left uninstrumented; not a skipped step.
