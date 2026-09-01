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
