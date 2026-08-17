---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators would rather have honest gaps than guessed commands]]
[[What is in the 33 queue entries no tool has ever listed]]

**The idea.** Instrument-writing is gated on repo sight. A surface without it gets a refusal instead of a write, and the test routes to a named lane (work waiting on an attended pass) rather than being cleared blind.

**Why this shape.** It is the only candidate that makes the guarantee unconditional — every instrument in the tree was written by something that had read the code, and the cost is paid visibly as a named backlog rather than silently as guessed paths. It also answers what a blind pass should *do* with `solutionsMissingInstruments`: nothing, and say so — which many sweeps have now done by hand.

**Comparison to siblings.** "An instrument records whether the pass that wrote it could see the repository" is the observe-only floor; this is the ceiling — both could ship, in that order. "An instrument naming a spec path that does not exist is refused" catches a weak artefact even from a sighted author, which this rule alone does not.

**Where it fails, stated so it can be judged.** Trades throughput for groundedness at an unknown exchange rate: under this rule an unattended fleet contributes zero instruments to a backlog that (see below) turns out to be almost entirely non-mechanical anyway. The blunter risk: gating on capability argues for handing an unattended loop repository access, which is a distinct safety conversation and should be had deliberately, not as a side effect of this rule.

**Cost.** A capability check and a lane. Small to build, large to live with.

**Definition of done.** "Five operators choose between sixty-one weak instruments and sixty-one blanks" — deliberately no command; this solution trades throughput for a preference no repository can hold, so it is `humansRequired` by design. A builder should not start this until that result exists.

## The standing finding — established 2026-08-10, reconfirmed every sweep since

**The queue's blocker is composition, not sight, and this was proven rather than assumed.** A complete census (2026-08-10) opened every test beneath all 58 entries then in `solutionsMissingInstruments` — not just their solution's title — and classified each by what its test could actually measure:

| Class | n of 58 | What it actually needs |
|---|---|---|
| A person is the measurement (pricing, positioning, willingness) | 40 | An interview or an operator's answer |
| Elapsed calendar time is the measurement | 7 | Weeks of ordinary running, not a spec |
| Already `status: shipped`, listed anyway | 7 | Nothing — a green-on-arrival command measures nothing |
| No command by design, stated in the node's own body | 1 | This node |
| Premise superseded by the product already existing | 1 | — |
| Threshold conflates a mechanical clause with a human one | 2 | Splitting the test — a structural edit, not an unattended pass's call |
| **Genuinely mechanical** | **0** | — |

Two firings that *held* repo sight (`ost_read_repo` answering, or built-in `Glob`/`Read` access confirmed live) wrote **zero** instruments anyway, because there was nothing in the queue a command could settle — the strongest possible refutation of "sight is the blocker." One further finding, useful for any future gate design: `ost_read_repo` and built-in file tools (`Glob`/`Read`) are **separable grants** over the same directory — a pass can hold one and not the other, observed both ways across different firings on the same machine.

**The queue has grown since (58 → 70, stable at 70 through 2026-08-17) purely by new solutions entering already-classified families** — commercial/pricing, axiom/goal-acquisition, highlight-digest, CONVO opportunity-grammar — and every new entrant checked has landed `people` or `elapsed-time`, never mechanical. The one near-miss worth a future builder's attention: "Every new sibling opportunity states its differentia at creation, or the create is refused" is genuinely code behaviour (a create-time guard), but its current test asks whether the differentiae authors write are *good*, which no exit code holds — splitting it into a feasibility half (guard refuses without a differentia) and a desirability half would give this queue its first real mechanical entry. That split is a human/attended-pass call.

**A related batch defect, still unfixed:** tests created with `lane: humans-required` at creation still surface their solution in `solutionsMissingInstruments` on the next sweep — reproduced across at least three separate founder-theory/highlight batches. The repair belongs to "Work I already finished keeps coming back in the queue, so the pass can never say it is done", by excluding humans-required-laned tests from this bucket's count.

⚠️ Unvalidated. Agent-ideated.

## History
- 2026-08-07 → 2026-08-11: repo-sight-gating hypothesis tested directly across ~14 firings, both with and without the grant; queue moved 58 → 70 purely via new non-mechanical entrants. `mechanical = 0` held at every recount.
- 2026-08-17 body compressed (this edit) — 14 dated "not a recorded result" entries folded into the standing finding above; nothing dropped, see git log.
- 2026-08-17 body edited — 14 dated "not a recorded result" entries (2026-08-07 through 2026-08-17) grew this node to 38KB restating the same finding — the queue's blocker is composition, not repo sight. Compressing to the standing finding plus a compact trend log, following the same precedent already applied to the Outcome node (2026-08-04) and to the sibling ledger node on this same pass. No claim dropped; git history holds the full prior text.

## Issues
- 2026-08-07 A human-required test still reads as instrument debt (see "batch defect" above) — this node's own only test, "Five operators choose between sixty-one weak instruments and sixty-one blanks", is itself an instance: created `humansRequired` correctly, and still listed in `solutionsMissingInstruments` on the very next sweep. `ost_flag_humans_required` is withheld from the unattended surface, so this cannot be relabeled from here.
- 2026-08-17 Queue held at 70 with no new family since the highlight-digest batch (2026-08-11). Composition finding unchanged; no repo-sight grant held this sweep (by design — see "What this surface withholds").
