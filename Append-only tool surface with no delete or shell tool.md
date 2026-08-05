---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A full discovery pass can be completed with no delete and no edit tool]]

**Candidate solution (unvalidated).** The entire toolset offered to the agent is create / append / annotate / set-status only — there is deliberately no delete, edit, or shell tool. Destruction is impossible because the capability is absent, not merely discouraged.

**Approach:** *safety by construction* — remove the dangerous verbs.

**Contrast with siblings:** unlike the git-substrate solution (which makes harm revertible) this makes harm unexpressible in the first place; unlike push-off-by-default (containment) it addresses local action, not exfiltration.

_Addresses: "Fear the agent could take a destructive, irreversible action". Related to "Want proof no hijackable capability even exists". Unvalidated — human to review._

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test can a full pass be done with no delete or edit tool" — moved under "A full discovery pass can be completed with no delete and no edit tool" — the belief this test measures now has a node of its own

## Issues
- 2026-08-04 Possibly stale, and left un-instrumented for that reason. This solution's premise — that the tool surface has no delete or edit tool — no longer describes the product: `ost_edit_node`, `ost_detach_nodes` and `ost_merge_nodes` all exist and this pass used all three. Its test, "Test can a full pass be done with no delete or edit tool", therefore asks a question the product has already answered in the negative by moving on.

I did not write an instrument for it, because any command I chose would be measuring a design the product has left, and a red-today spec for abandoned behaviour is worse than no spec — a builder could pick it up and implement it. I also did not set it `deferred` or merge it away: whether the append-only surface was the right thing to leave is a product judgement, and the tree still carries live needs about irreversibility ("A call the tool should have refused is permanent, because append-only cannot take it back") that this node's reasoning bears on.

For a human: decide whether this is (a) superseded and should be `deferred` with a note pointing at what replaced it, or (b) still a live alternative, in which case its body needs rewriting to argue against the current surface rather than describe it. Flagged rather than actioned because both readings are defensible and choosing between them is not the sweep's call.
- 2026-08-05 2026-08-05 The 2026-08-04 staleness finding above is confirmed rather than merely repeated, and by the same means: this unattended sweep again used the mutating tools whose absence this node's premise asserts. `ost_edit_node`, `ost_detach_nodes` and `ost_merge_nodes` are all on the sweep's granted surface, and the sweep's own instructions now state the replacement rule outright — the vault is no longer append-only, and what replaced it is a narrower guarantee: reserved sections (`## Results`, `## Uncovered`, `## Instrument Log`) can be neither authored nor destroyed, `## History` stays append-only, retraction is a human's CLI call, and git holds every write. So the product did not abandon safety-by-construction; it moved the construction from "no dangerous verbs exist" to "the verbs that would let an agent forge or revoke a human's finding do not exist". That is a materially different claim from the one this node makes, and it is arguably the stronger one, since the previous surface's own failure is already recorded in this tree as "A call the tool should have refused is permanent, because append-only cannot take it back". I am leaving the node un-instrumented and un-deferred for the reason the prior pass gave — a red-today spec for abandoned behaviour is worse than no spec, because a builder could pick it up and implement it — and repeating the ask, now with the successor named: a human should either defer this with a pointer to the reserved-section guarantee that replaced it, or rewrite its body to argue that removing the verbs entirely was better than constraining which ones exist. Two passes have now declined to make that call, which is itself worth knowing.
