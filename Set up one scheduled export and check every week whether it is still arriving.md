---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: '8 of 8 weekly checks find a current file, with no silent gap.'
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a scheduled export, once configured, keeps arriving. The failure this solution's own reasoning fears is a silent stop — an expired link, a renamed sheet — which looks identical to an experiment that produced nothing. If that happens quickly, the route replaces a human who forgets with a mechanism that fails invisibly.

**Risk category: feasibility.**

**Design.** Configure one export from a real source into the watched folder. Each week for eight weeks, check whether the expected file arrived and whether its contents are current. Record every gap and its cause.

**Why it is small.** Configuration only, no code, and the checking is a minute a week.

**What it will not cover.** Eight weeks will not catch annual credential expiry, which is a likely cause of exactly this failure. It also tests one source configured carefully by someone who knows it matters.

## 2026-09-02 unattended sweep — examined for an instrument, and it cannot take one

Recorded here so no future pass re-derives it. This test was one of the four remaining genuinely-unexamined entries named in the residue on "The biggest queue on my report is one the surface reading it to me has no tool to clear".

**Verdict: not repo-answerable, and the deciding artefact is outside this repository twice over.** The threshold is "8 of 8 weekly checks find a current file, with no silent gap." What is being observed is a third-party export — someone else's sheet, someone else's credential, someone else's scheduler — continuing to deliver into a watched folder across eight weeks. This product's suite can test that the watcher notices a file and can test how a gap is reported, and neither is what this test asks: it asks whether the external producer keeps producing. A spec cannot hold a credential that has not expired yet, and the body already concedes that even eight weeks will not reach the likeliest cause, annual expiry.

**Worth separating for whoever builds here.** The failure this test fears — a silent stop that looks identical to an experiment that produced nothing — is a distinguishing question the repository *could* answer, and the tree already carries it separately as "A scheduled export keeps arriving, and a stopped one does not look like an empty experiment". That one is about the reporting and is instrumentable in principle; this one is about the external world's persistence and is not. Splitting them is why this node stays uninstrumented rather than being handed a command that answers its neighbour.

**What the repair is, and why this pass cannot make it.** A person watching a real external source over eight weeks is the measurement, and the frontmatter carries no lane saying so. `ost_flag_humans_required` is withheld from the unattended surface by design; the fix is one `ost-agent lane --set` naming this test humans-required.

_Nothing was executed, no instrument set, no lane set, no rung moved, no status changed. Read first-party from disk during the 2026-09-02 unattended sweep._
