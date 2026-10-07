---
type: Solution
created: '2026-08-05'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A refusal written down once will actually be read before the next call that would repeat it]]

**The mechanism: give the correction a carrier.** When a guard refuses a call, the refusal is appended to a durable per-workspace ledger — what was attempted, what it was refused for, and the permitted form. A session reads that ledger before it composes anything, so the seventh occurrence of `sleep 45 && gh pr checks` never gets written, because the session already knows how that ends.

**Why this shape.** It is the smallest change that makes the guard stop being the only memory in the system. Nothing about the refusal logic changes, nothing about the tool surface changes; the message simply stops evaporating when the session does. The evidence supports it directly — the same refusal on seven sessions across four days is not a reasoning failure, it is a storage failure, and storage is cheap.

**Compared to its siblings.** The only one of the three that carries *reasons* rather than just outcomes, which matters because refusals are not all alike and a ledger entry can say what the permitted form was. It is also the only one that works for corrections nobody has yet turned into a constraint — a guard can refuse something long before anyone has decided how to make it unexpressible. Against that, it is the one that depends on the reader actually reading: it adds a document to be consulted, and the whole premise of the problem is an agent reaching for a reflex rather than consulting anything.

**What would make this the wrong pick.** A ledger that grows without bound becomes a thing nobody reads, which is the exact failure it was built to fix, one level up. It also puts the correction in the same place as the reflex — inside the composer's judgement — and a reflex that survived seven explicit refusals may well survive a note about them.

⚠️ Unvalidated. Agent-ideated on 2026-08-05 from machine-captured session friction, by the agent whose own repeated failure the evidence records — which is a reason to discount its confidence that a note to itself would have helped.

## Definition of done

"Replay the seven refusals and check the ledger surfaces every one before a call is composed"

`npx vitest run test/loop/corrections-ledger.test.ts`

Proves delivery, not persuasion: the seven observed refusal classes are in the ledger exactly once each with their permitted form, and all seven reach a session before its first composed call. Red today because nothing outlives the session a refusal was issued in.

## History
- 2026-08-05 unlinked "Replay the seven refusals and check the ledger surfaces every one before a call is composed" — moved under "A refusal written down once will actually be read before the next call that would repeat it" — the belief this test measures now has a node of its own

## 2026-10-07 — the shipped ledger drops the most-repeated refusal in this workspace, by its own rule

The ledger now exists (`src/loop/corrections.ts`), and this firing was handed its briefing, "CORRECTIONS ALREADY ISSUED IN THIS WORKSPACE", before composing anything. The briefing carried two entries: the sleep-then-poll block and "No such tool available: Bash". Then this firing's fourth call was a `Grep` on `/Users/tanner/dev/OST-Agent/src/eval/buildable.ts`, and it was refused with "Claude requested permissions to read from …, but you haven't granted it yet." In the 46 transcript records captured 2026-10-05 to 2026-10-07, eleven carry that same denial and eight of them name the same file. The sibling node "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed" counts it at 298 occurrences across 272 records as of 2026-10-06. The sleep block, the ledger's founding case, is thirteen sessions.

**Why the briefing never mentions it. Read first-party this pass, not inferred.** `splitRefusal` keeps a refusal only when a sentence near its end carries a remedy cue (`REMEDY_CUES`: use / must / instead / try). The module's header says a refusal that names no alternative "is dropped, deliberately and visibly." The permission denial contains none of the four words, so it is dropped. It probably also fails the earlier `GUARD_MARKER` check, because the harvested text of this denial shows no `<tool_use_error>` wrapper, while the "No such tool available" refusal in the same records does. That second point is read from evidence bodies, not from a raw transcript, so it is the weaker of the two.

**What that means for this candidate.** The design assumed that a correction *is* its remedy, and keyed the ledger on the permitted form. That holds for refusals whose guard knows the alternative. Here the guard does not know it, but the workspace does: `ost_read_repo` reads the same file on the same pass, as this node's sibling has shown repeatedly and as this firing did again. So the remedy is known, just not to the code that issued the refusal. The ledger has no way to attach a remedy it was not told, and the rule that keeps it short is what keeps this refusal out of it. This is the "depends on the reader actually reading" risk this node already names, arriving from the other side: the reader would have read it, but nothing wrote it down.

**Not proposed here, and left for whoever weighs this candidate:** an operator-authored remedy for a remedy-less refusal (e.g. "for paths under the product repo, use `ost_read_repo`") would keep the ledger keyed on remedies without the guard having to know one. Whether that belongs in this ledger, in the repo-sight preflight, or in a granted permission is a design choice. It is not this pass's to make, and no node was created for it.

_Method: first-party `ost_read_repo` of `src/loop/corrections.ts`, a Grep over this vault's evidence store for the denial text in records fetched 2026-10-05 to 2026-10-07, and this firing's own refused call. These are observations of this agent's own surface. They ground feasibility and usability, not desirability. Nothing executed, no instrument set, no rung moved. `ost_check` is withheld on this surface, so this write has not been verified by the invariant checker._

**Correction to the counts in the 2026-10-07 section above. They were too low.** I wrote them from a partial grep. The complete count, over all 43 transcript records fetched 2026-10-05 to 2026-10-07: **19 carry the permission denial, 17 of them on a path under `/Users/tanner/dev/OST-Agent`, and 10 name `src/eval/buildable.ts` specifically.** The section said "eleven" and "eight". The finding does not change, and it is stronger with the true figures: in the last three days about four firings in ten were refused the same remedy-less call, and the ledger carried none of them.
