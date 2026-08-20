---
type: Solution
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: what is deliberately given up — the TTL's self-healing.** `src/loop/claim.ts` releases a claim in exactly two ways: an explicit `released` record, or `DEFAULT_CLAIM_TTL_HOURS = 8` elapsing. The module's own header names the consequence: "too long and a pass that dies mid-build strands the item until the clock runs out" — so it chose a clock. This candidate chooses the other horn: a claim carries the branch (or PR number) it produced, stays `held` past its TTL while that branch is unmerged and open, and is released when the branch merges or the PR closes. The clock survives only for claims that never produced a branch at all — the dead-mid-build case the TTL was for.

**The idea.** Claiming already happens at the start of a build, so the extension is to write the branch name into the claim record when the build pushes, and to have `liveClaims` consult `git branch -r --merged origin/main` (or `gh pr view --json state`) before declaring a held claim expired. A finished-but-unmerged build is then exactly what the claim ledger says it is: taken, by a named session, with a named branch, until trunk says otherwise.

**Against its siblings.** Keeps the decision inside the mechanism the parent opportunity already built for "taken", rather than adding a second detector ("Target selection skips…") or a new permission ("The ship step merges…"). It is the only sibling that also records *who* holds the work, which a refusal can quote.

**Where it fails, stated so it can be judged.** The two observed targets (#130, #181) were never claimed — the claim module landed after those builds started — so this fixes the next occurrence, not the recorded ones. A PR abandoned open holds its claim forever unless something closes it; that is the stranding the TTL prevented, now traded for the re-selection the TTL caused. Checking merge state needs the product checkout or the forge to be reachable from the state directory, which the claim module deliberately does not assume today.

**Cost.** A field on `ClaimRecord`, a merge-state check in `isLive`, and a decision about what "closed without merge" means for the claim.
