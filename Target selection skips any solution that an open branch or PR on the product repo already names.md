---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: when it acts — at selection time, before any model call.** The preflight in `build-pass.sh` already narrows candidates mechanically (`gate`, `buildable`); this adds one more mechanical filter in the same place: a candidate whose title resolves to an open branch or open PR on the product checkout is dropped from the buildable list and named in the report as "finished, awaiting merge" rather than built.

**The idea.** The information the loop needs is already on disk — `git branch --list`, `git log origin/main..<branch>`, and `gh pr list --state open` — and none of it costs a model call. Resolution is the hard half, and `src/loop/claim.ts` has already solved it once: a branch name (`run-tool-surface`) is a *naming*, and `resolveWorkItem` resolves a naming against a document of items. Here the document is the buildable list itself, so the same matcher, the same vocabulary argument, and the same refusal shape ("unresolved is not free") apply.

**Against its siblings.** Cheapest and least trusting: it changes nothing about what the loop may do to the world, only what it may choose. "The ship step merges its own green PR" removes the window by finishing the job but needs a permission the operator has not granted; "A work claim released by the merge" fixes the claim ledger but only for work that was claimed, and the two observed targets predate claiming. This one catches the case regardless of how the first build started.

**Where it fails, stated so it can be judged.** A branch whose name shares no vocabulary with the solution title (claim.ts's own Jaccard-0.29 example) resolves to nothing, and the filter does nothing. An abandoned branch left open forever would hide a target indefinitely, which is the same stranding risk claim.ts accepts for a TTL — the report has to name what it skipped, or this manufactures a silent hole in the queue.

**Cost.** One resolution call per candidate, one `gh` call per firing, and a branch-naming convention for builders to follow.
