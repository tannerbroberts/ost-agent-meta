---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: 'At least 2 of 10 ask about terms, trial, or invoicing.'
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that a maintained tree is worth a recurring payment. The value is invisible in exactly the months when nothing much happened, and a subscription whose best months look like its worst is a hard subscription to keep.

**Risk category: viability.**

**Design.** Make a concrete offer to ten teams: your product's discovery tree, kept current, at a named monthly price. Do not soften the price or offer a free tier. Count how many ask about terms, a trial, or an invoice — the behaviours that precede paying — as against those who say it sounds interesting.

**Why it is small.** Ten conversations against an offer that already describes a thing the tool does. Nothing is built and no tree need be delivered unless someone says yes.

**What it will not cover.** Asking about terms is not paying, and the ladder ranks it below money accordingly. It also says nothing about renewal, which is where the invisible-value problem actually bites.

A human runs this and records the result.

## Issues
- 2026-08-17 Lane unset, and this sweep could not set it. This test is humans-required, not instrument-able: design says "Make a concrete offer to ten teams" and count who asks about terms/trial/invoice — a real prospective buyer's reaction to a live offer, not computable. `ost_flag_humans_required` is withheld on this unattended surface (see the "what this surface withholds" list), so the judgement is recorded here instead. Left for a human: `ost-agent lane "Offer a maintained tree at a stated monthly price to ten teams and count who asks for terms" --set humans-required`.
