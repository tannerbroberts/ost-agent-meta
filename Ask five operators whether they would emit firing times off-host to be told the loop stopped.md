---
type: AssumptionTest
source: 'agent-ideation:2026-09-07-unattended-sweep'
created: '2026-09-07'
evidence: assertion
lane: humans-required
threshold: at least 3 of 5 operators say they would enable it
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: viability.**

**The design.** Put the trade to five operators in concrete terms rather than in principle: this product would send one message per firing to a service outside your machine, carrying the fact and time of the firing and nothing else; in return it tells you when firings stop arriving. Ask whether they would turn it on, and — the half that carries the information — ask what would have to be true for the answer to change. Record the reason alongside the verdict, because a "no" that means "not to a vendor" points at a self-hosted endpoint while a "no" that means "nothing leaves this box" retires the candidate outright.

**Pre-committed bar, stated before running:** at least 3 of 5 operators say they would enable it. Below that, this candidate is not viable in the form written and the two in-host siblings are the live options despite their blind spots.

**Why a person is irreducibly the measurement.** The question is what someone would accept, and the only recorded evidence bearing on it in this vault is the founder's own default of `remote.enabled: false` — one person, and the person who wrote the default. Asking outside operators is the whole point, since this tree's mandate names external returning operators as the instrument that keeps it from grading its own homework.

**What this does not settle.** Nothing about whether the mechanism detects outages correctly, and nothing about the two siblings' relative merits. It answers only whether the switch would ever be turned on.

Proposed only. A human runs this; this pass did not.

A person outside the building is the measurement here: Willingness to give up local-only operation is a preference held by people outside this codebase; no exit code observes whether anyone would flip the switch, and the operators must be asked directly.
