---
type: Assumption
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
---
#Assumption #unvalidated #evidence/assertion
[[A claim whose branch landed by merge commit, squash, or rebase reads as released from the checkout alone]]

**Kind: feasibility.** Releasing a claim on merge requires knowing a merge happened. The cheap read is `git branch -r --merged origin/main`, which answers by ancestry — and a squash merge (the default for many `gh pr merge` setups, and what a one-commit-per-PR trunk looks like) leaves the branch's commits *outside* main's ancestry. The branch then reads as unmerged forever, which turns "released by the merge" into "never released": the exact stranding the TTL was there to prevent, now with no clock to save it. The alternative read, `gh pr view --json state`, answers correctly but needs the forge reachable and authenticated from the loop's state directory, which `claim.ts` deliberately does not assume.

**Stated so it could be false:** for each of the three merge styles a PR can land by (merge commit, squash, rebase), the checkout alone yields a correct merged/unmerged answer for the claim's branch.

**What would change if it were false.** The claim must record the PR number rather than the branch and ask the forge, or the loop must delete merged branches as part of shipping so "branch absent" becomes the signal. Either is buildable; neither is what the solution's body describes.
