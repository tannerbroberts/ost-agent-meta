---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[Test can a full pass be done with no delete or edit tool]]

**Candidate solution (unvalidated).** The entire toolset offered to the agent is create / append / annotate / set-status only — there is deliberately no delete, edit, or shell tool. Destruction is impossible because the capability is absent, not merely discouraged.

**Approach:** *safety by construction* — remove the dangerous verbs.

**Contrast with siblings:** unlike the git-substrate solution (which makes harm revertible) this makes harm unexpressible in the first place; unlike push-off-by-default (containment) it addresses local action, not exfiltration.

_Addresses: "Fear the agent could take a destructive, irreversible action". Related to "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule

## Issues
- 2026-08-04 Possibly stale, and left un-instrumented for that reason. This solution's premise — that the tool surface has no delete or edit tool — no longer describes the product: `ost_edit_node`, `ost_detach_nodes` and `ost_merge_nodes` all exist and this pass used all three. Its test, "Test can a full pass be done with no delete or edit tool", therefore asks a question the product has already answered in the negative by moving on.

I did not write an instrument for it, because any command I chose would be measuring a design the product has left, and a red-today spec for abandoned behaviour is worse than no spec — a builder could pick it up and implement it. I also did not set it `deferred` or merge it away: whether the append-only surface was the right thing to leave is a product judgement, and the tree still carries live needs about irreversibility ("A call the tool should have refused is permanent, because append-only cannot take it back") that this node's reasoning bears on.

For a human: decide whether this is (a) superseded and should be `deferred` with a note pointing at what replaced it, or (b) still a live alternative, in which case its body needs rewriting to argue against the current surface rather than describe it. Flagged rather than actioned because both readings are defensible and choosing between them is not the sweep's call.
