---
type: Assumption
source: 'REPO:OST-Agent/src/loop/wait.ts'
created: '2026-10-02'
evidence: assertion
authorship: machine
---
#Assumption #unvalidated #evidence/assertion

**Risk category: feasibility.**

**The belief, stated so it could turn out false:** the `await` shim that `renderWaitShim()` in `src/loop/wait.ts` emits can keep a record keyed on the condition between two separate invocations, so the second wait on the same condition sees the seconds the first one spent and can extend its own bound. It has to do this without losing the contract the existing spec pins: exit 0 when the condition holds, the condition's own status plus a `gave up after` line on stderr when it does not, and exit 2 when no condition is named.

**Why this is the belief and not a formality.** Today the shim is stateless by construction: `waited=0` is set on every run and nothing is written anywhere. That was checked this pass with a first-party read of the whole file (untruncated). The shim is also deliberately plain POSIX `sh` with "nothing baked in at install time", per the module's own doc comment. So any per-condition record has to live somewhere a bare `sh` script can reach without a configured path. Where it lives, and whether a parallel or renamed wait corrupts it, is the open part. The sibling belief "Conditions that expire are more often genuinely slow than never going to be true" is about whether escalation is *wise*. This one is about whether the shim can carry it at all, and the two can come out differently.

**Why it was added now.** Until 2026-09-20 this solution recorded that the helper was "supplied by the harness, not in this repository", and every pass that declined to instrument it relied on that claim. The 2026-09-20 section on the solution corrected it, and this pass re-read the source and found the same thing. That leaves a repo-answerable belief that the tree did not yet hold.

⚠️ Unvalidated. Added by an unattended pass on 2026-10-01. It does not argue that the candidate should be built. Whether it should depends on the separate engagement count on the solution.
