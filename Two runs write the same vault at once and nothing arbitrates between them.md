---
type: Opportunity
status: unvalidated
source: >-
  tree-restructure:2026-08-05 — split from the bucket that held these solutions
  directly
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[One writer at a time, enforced by a lock the second agent waits on rather than ignores]]
[[Each agent writes on its own branch, and merging is a deliberate, reviewable step]]
[[Detect drift at write time and refuse, naming what changed since the read]]

There is no lock, no branch, and no drift check. Two agents reading the same state and writing back their own version of it is an ordinary occurrence rather than an edge case, and the loser's work disappears without either run noticing.

## 2026-08-31 — the vault write race, caught happening, for the first time in this corpus

This node has carried three candidate solutions and no observed instance since it was split out on 2026-08-05. It has one now, and it arrived in this firing's own ingest.

**The record.** `TRANSCRIPT:745e5409-ef82-4c5c-9b07-2b6f63ec44dc`, session timestamped 2026-09-01T00:48:52Z, mirrored 0d ago. Five friction events. The first is a `tool_error` on `mcp__ost-agent__ost_create_node`:

`fatal: cannot lock ref 'HEAD': is at eecffa5489c2af1ef694c0d5938b33eb284f38fb but expected c1ba5dad2dd2d7209ed9c1132e234f121b3006e8`

That is git refusing a ref update because the ref moved between the read and the write. The failing call is an OST tool's own auto-commit against this vault. So two writers were inside the same commit window on this vault, and one of them was a node creation.

**Why this belongs here and not on the parent's existing corroboration.** The parent, "Two agents sharing my vault can trample each other", carries two prior sightings and closes them with an explicit caveat: "both concern the source repository rather than a vault; whether that generalises to two agents on one vault is an inference a human should rule on, not a fact these records establish." This record is the vault. The inference the caveat asked a human to rule on is no longer an inference for the write-race half — that half is now observed. The decision-collision half the parent describes is untouched by this and stays where it is.

**A correction to this node's own wording, which matters for choosing between its three candidates.** This node says "the loser's work disappears without either run noticing." On this instance it did not. The write failed loudly, named both hashes, and the caller saw an error. Git's ref lock is itself a last-resort arbiter: it refuses rather than corrupts, at the last possible moment, at the cost of a failed tool call. So the accurate statement of the need is narrower and, if anything, more tractable — there is no arbitration *before* the write, and the only thing standing between two runs is a substrate refusal that fires after the work of composing the call is already spent.

**What this does to the three candidates beneath.** It bears most directly on "Detect drift at write time and refuse, naming what changed since the read", because the substrate already implements a crude version of exactly that: refuse at write time, naming what changed — as two hashes. That candidate's remaining value-add is naming *what* changed in terms the agent can act on rather than which commit it was, and whoever weighs the three should weigh it against a baseline that is already partly present rather than against nothing. It says less about the lock and branch candidates, both of which would act earlier than the substrate does.

**What it does not establish, stated so it is not over-read.** One occurrence. It gives no rate, and this signature appears exactly once across all 534 transcript records on disk — checked this pass by grep over the vault's own evidence directory — so it is rare rather than routine on the evidence available. It does not establish that any node was actually lost: the tool call errored, and whether that firing retried, and whether a half-written node was left behind, is not visible in the record. It says nothing about two *operators* colliding, which remains unmeasured.

**One adjacent open ask it partly informs.** The standing humans-required test "Ask the operator whether firings on the shared checkout can ever overlap in time" asks whether the scheduler ever lets two firings run at once. This record shows two writers inside one commit window on the vault, which is evidence that the scheduler does permit overlap — but the ask is about the product checkout, not the vault, and they are different repositories. It narrows that question; it does not answer it, and answering it is still the operator's.

_Method: this firing's own `ost_ingest_inbox` output, the evidence body via `ost_next_work({evidence})`, and a grep over `.ost-agent/evidence/` for the signature. Nothing executed, no test run, no result recorded, no rung moved. Observed behaviour of this product's own agent — it grounds usability, not desirability._

## 2026-09-02 — a second instance, from a different git mechanism, and the rate claim above is a floor rather than a measurement

Kept short. One correction to this node's own arithmetic, checked first-party.

**The claim being corrected.** The 2026-08-31 section closes its limits paragraph with: "this signature appears exactly once across all 534 transcript records on disk — checked this pass by grep over the vault's own evidence directory — so it is rare rather than routine on the evidence available." The word doing the work is *signature*. That pass grepped for the string it had just observed — git's ref-lock refusal, `cannot lock ref 'HEAD': is at … but expected …`. A concurrent-writer collision does not have one string.

**The second instance.** `TRANSCRIPT:c76af6ce-fa7e-44dd-b4a2-4ff8d40e25c4`, session timestamped 2026-08-29T21:14:53Z — three days *before* the record the section above calls the first sighting in this corpus. Four friction events; the first is a `tool_error` on `mcp__ost-agent__ost_ingest_inbox`:

`fatal: Unable to create '/Users/tanner/ost-agent-meta/.git/index.lock': File exists. Another git process seems to be running in this repository`

The path names this vault, not the product checkout, so no generalisation step is needed. The two events following it are both retries of the same call.

**Why it is the same need and not a new one.** Both are one writer's auto-commit refused because another writer held the repository. They differ in which lock fired: the index lock is taken at the *start* of a commit and refuses a second writer outright, while the ref lock is checked at the *end* and refuses only if HEAD moved underneath. So the two records catch the same race at opposite ends of the same operation, through two different OST tools — `ost_ingest_inbox` and `ost_create_node`.

**What that does to this node, in three directions.**

- **The count is two, not one, and it is still a floor.** Both instances were found by grepping for a message somebody had already seen. Git has more of these — `index.lock` and ref-lock are two of several — so any count built this way measures the signatures a reader thought to look for. Nobody has yet enumerated the class.
- **The 2026-08-31 correction to this node's wording holds, and gets stronger.** That section observes the loser's work does *not* disappear silently: the substrate refuses loudly. The index-lock case refuses even earlier and more cheaply — before the commit starts rather than after composing it — which sharpens the same point. There is still no arbitration before the write; there are two substrate refusals of differing lateness.
- **It bears on the same candidate, and slightly differently.** The 2026-08-31 section argues "Detect drift at write time and refuse, naming what changed since the read" competes against a baseline git already partly provides. The index-lock instance is not drift at all — nothing changed since the read; a second process simply held the lock. That is the case the lock candidate, "One writer at a time, enforced by a lock the second agent waits on rather than ignores", addresses directly and the drift candidate does not: here the right behaviour is to *wait*, not to report what moved. Whoever weighs the three should note the two records point at two different candidates.

**What it does not establish.** Two occurrences across the corpus is not a rate, and this pass did not enumerate git's other contention messages, so it cannot say the true count is not higher. It does not show either firing lost work — both records show a retry after the failure and neither shows the outcome. It says nothing about two *operators* colliding, which is still unmeasured, and nothing about desirability.

**One thing a human may want to change that this pass did not.** This node's rung is `assertion` while its body now rests on two machine-captured records. Its `source` is `tree-restructure:2026-08-05`, not a recording, and the ladder caps the measurement rungs by what the source has earned — so `ost_set_evidence` to `observed` would be refused here on provenance grounds even though the evidence beneath it is observed. That is a labelling question about this node's source field, not a judgement about the evidence, and it is left alone deliberately.

_Method: grep over `.ost-agent/evidence/` in this vault for git contention strings other than the one the prior section searched, plus a first-party read of the record named above. Nothing executed, no test run, no result recorded, no rung moved, no node created. Observed behaviour of this product's own agent — it grounds usability, not desirability. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design._
