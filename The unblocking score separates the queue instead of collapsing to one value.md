---
type: AssumptionTest
source: 'agent-ideation:2026-09-01-unattended-sweep'
created: '2026-09-01'
evidence: assertion
threshold: no more than 75% of queue entries share the single most common leverage score
instrument: npx vitest run test/ost/ask-queue-leverage-order.test.ts
sight: grounded
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

Compute the unblocking score over the ask queue and check two things.

**That it sorts on structure, not on dates.** Build a fixture with two ageless entries: one is the sole test under an assumption carrying several solutions, the other unblocks nothing. Assert the first leads. Then give both contrasting `askedAt` values and assert the order is unchanged — that is what makes this candidate distinct from its siblings rather than a second clock.

**That it does not collapse.** Score this vault's own 62 queued tests and take the share sitting on the most common value. Above three quarters and the ordering is flat, which refutes the parent assumption on exactly the ground it names — the fourth instance of a constant field dressed as a ranking key — and the candidate should be killed rather than tuned.

**Why this instrument is red today, stated honestly.** `test/ost/ask-queue-leverage-order.test.ts` does not exist, so this is a `no-spec` red: it fails for the reason any question written on that path would fail, mints no build permit, and the test is unfinished until the file exists and an assertion inside it fails. The instrument surface accepts one bare spec-file command and refuses shell punctuation, so the stronger form — an existing spec named with a `-t` filter on the missing assertion — could not be written here.

**What this does not settle.** Whether the order is any *good*. A distribution that separates is not the same as a ranking the operator agrees with, and this candidate's real claim — that leverage is a better question than elapsed time — is a judgement no exit code reaches. It also cannot see the cost this candidate openly accepts: an ask that unblocks nothing sinks permanently and stops being surfaced as neglected, which is a commitment `src/knowledge/asks.ts` made and this candidate declines. A green here says nothing about whether declining it was right.
