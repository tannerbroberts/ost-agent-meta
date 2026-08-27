---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-safety-requirement.md'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Solution #ported-from-ost-agent-vault #evidence/assertion
[[A full discovery pass can be completed with no delete and no edit tool]]

**Candidate solution (unvalidated).** The entire toolset offered to the agent is create / append / annotate / set-status only — there is deliberately no delete, edit, or shell tool. Destruction is impossible because the capability is absent, not merely discouraged.

**Approach:** *safety by construction* — remove the dangerous verbs.

**Contrast with siblings:** unlike the git-substrate solution (which makes harm revertible) this makes harm unexpressible in the first place; unlike push-off-by-default (containment) it addresses local action, not exfiltration.

_Addresses: "Fear the agent could take a destructive, irreversible action". Related to "Want proof no hijackable capability even exists". Unvalidated — human to review._

## Standing finding: the premise is half superseded, and the split needs a human

Established 2026-08-04 and reconfirmed by every sweep through 2026-08-10 — seven passes, each verifying it the same way, by using the tools whose absence this node asserts.

**The half that is false.** The vault is no longer append-only. `ost_edit_node` replaces prose, `ost_detach_nodes` removes an edge, and `ost_merge_nodes` folds a duplicate away and deletes its file outright — a real delete. All three are on the unattended sweep's surface, and the ruleset now directs passes to *prefer* merging duplicates over annotating them. The assumption beneath this node, "A full discovery pass can be completed with no delete and no edit tool", has been answered in the negative by the product's own design rather than by any test.

**The half that is true and still shipped.** There is no shell tool. Verified against the code on 2026-08-10: `examples/automation/autonomous-pass.sh` denies `Bash,BashOutput,KillShell,Edit,Write,NotebookEdit,Task,Skill,WebFetch,WebSearch`, so no shell reaches an unattended firing.

**What actually replaced the blanket rule, and it is arguably stronger.** The guarantee moved from "no dangerous verbs exist" to "the verbs that would let compute forge or revoke a human's finding do not exist": the reserved sections `## Results`, `## Uncovered` and `## Instrument Log` can be neither authored nor destroyed by any tool; `## History` is append-only and corrected by appending; `validated` is not a status an agent can set; retraction is a human's CLI call. That is a claim about *evidence* rather than about deletion, and it is the one that has been load-bearing. The old surface's own failure is already recorded elsewhere in this tree, as "A call the tool should have refused is permanent, because append-only cannot take it back".

## Why no sweep has instrumented this, and what is being asked

No honest instrument exists for this node as worded. A spec asserting "no delete tool" would go red today — which looks like a valid red and is not one: it would be measuring the absence of a feature that was added deliberately, and a builder could pick it up and implement it. That is worse than no spec. Seven passes have declined on that reasoning, and none has set the node `deferred` or merged it away either, because both available repairs change what the tree says was decided.

**The decision a human owes this node** is which of two it is:

- **(a) Superseded** — `deferred`, with a pointer to the reserved-section guarantee that replaced it, and the surviving no-shell-tool claim re-homed on a node of its own.
- **(b) Still a live alternative** — in which case the body needs rewriting to argue *against* the current surface rather than to describe a surface that no longer exists.

Both are defensible; neither is an unattended pass's call. That seven passes have now declined to make it is itself worth knowing, and is the reason this ask is stated once here rather than an eighth time below.

**One consequence worth flagging separately:** this node is the standing argument against "Refuse an instrument that passes on arrival", which proposes adding command execution to a write path. That objection deserves re-stating against what the surface actually guarantees now, not against append-only.

**Related, and no longer unchecked — closed 2026-08-27.** This paragraph used to name "Refuse a proving command whose exit code cannot report failure" and "Refuse a write whose content is empty or literally undefined" as siblings of the same era that "may have shipped too", and to ask a later pass to check them. Both checks have since been run and both nodes carry the answer on themselves, so the errand is retired rather than reissued:

- "Refuse a write whose content is empty or literally undefined" — `status: shipped`, verified 2026-08-09 by reading `test/ost/vault-write-guard.test.ts` in full. This pass re-read that spec first-party and confirms it is still present and still asserts the guard against `src/ost/vault.js`, across `annotate`, `appendToNode`, `appendUnderSection`, `createNode` and the optional notes on `setStatus`/`setEvidence`/`setLane`, with a positive control pinning that the guard cannot pass vacuously.
- "Refuse a proving command whose exit code cannot report failure" — `status: shipped` (v0.21.0, commit `87164d6`), verified 2026-08-10 by reading `test/loop/exit-laundering.test.ts` in full, including the must-not-refuse set that node itself called the half worse-if-wrong.

One thing the 2026-08-09 verification did not mention, noticed on this pass's re-read and recorded here because it bears on this node's own subject: `test/ost/vault-write-guard.test.ts` has since grown a second guard beyond the empty/undefined one — a wikilink split across a line break is refused at *every* free-text write parameter, `ost_create_node.body`, `ost_append_to_node.section`, `ost_annotate.issue`, `ost_set_status.note`, `ost_set_evidence.note` and `ost_flag_humans_required.why`, with a refused write asserted to land nothing and a refused `createNode` to leave no file. Its header states the reason in this node's own terms: on an append-only surface a wrapped link could never be cleared, because clearing it would mean shrinking a body and no tool shrank a body. That is a concrete instance of the trade this node exists to argue about — the write boundary, not the absent verb, is where the one-way door got closed — and whoever answers (a)/(b) should weigh it.

Nothing else about this node changed and the (a)/(b) ask above is unchanged.

## Issues
- 2026-08-21 Consolidated seven near-identical annotations (2026-08-04 through 2026-08-10) into the standing finding above. No claim dropped; git holds the prior text. The ask to a human is unchanged and is stated once: decide (a) or (b).

## History
- 2026-07-24 evidence: (none) → assertion — retro-labeled: sources are founder notes, the agent's own sessions, or model ideation — no external party involved; floor rung per the ladder's own rule
- 2026-08-05 unlinked "Test can a full pass be done with no delete or edit tool" — moved under "A full discovery pass can be completed with no delete and no edit tool" — the belief this test measures now has a node of its own
- 2026-08-21 body edited — Seven passes (2026-08-04, -05, -06 ×3, -07, -10) each appended a near-identical annotation making the same request of a human, growing the node to 11.6KB in which the same finding is restated seven times. Nothing was dropped: every distinct fact those entries established is folded into the standing finding below, and git holds the full prior text. Consolidating because a node whose ask is buried under six re-statements of itself is a node the human it is addressed to will not read — and because each future sweep that meets this node is being invited to append an eighth.
- 2026-08-27 body edited — The "Related and unchecked" pointer had gone stale and was sending future passes on an errand already run. Both siblings it named — "Refuse a proving command whose exit code cannot report failure" and "Refuse a write whose content is empty or literally undefined" — now carry status: shipped and full first-party verifications against the repository (2026-08-10 and 2026-08-09 respectively), each recorded on its own node. This pass re-read both nodes and read test/ost/vault-write-guard.test.ts in full through ost_read_repo to confirm before rewriting. Only that paragraph changed; the standing finding, the (a)/(b) ask to a human, and the Issues note are reproduced verbatim, and no eighth restatement of the ask was added.
