---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-two-loops-share-one-git-managed-vault-with-no-wr.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

**The need (operator's voice):** "I had a thinker loop and a builder loop working the same git vault. Nothing told either whose turn it was — the builder had to check for a clean tree and hope, and would have had to back off mid-work if the thinker were mid-commit."

**Why it matters:** unattended operation (the parent need) assumes the processes writing the vault coordinate. There is no lease, no queue, no write contract — so adding a second loop converts 'walk away safely' into 'walk away and hope the writers interleave kindly'. Observed at the moment of friction by the builder loop, 2026-07-24.

**Litmus (more than one way?):** yes — a lock/lease file, a write queue, single-writer-per-vault convention, or serializing loops through one scheduler are all distinct answers.

**Solution ideation deferred:** dogfood-lane need; expand when prioritized (see root Prioritization).

## History
- 2026-07-24 evidence: (none) → observed — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.

## Second sighting, and it is a different failure than the first — 2026-07-26

**A whole pass of build work was written, tested green, committed, and thrown away,
because another pass had already built the same feature six hours earlier.** Observed
first-hand by the pass that wasted it.

**What happened, with times.** A loop iteration cloned `tetrix-game-monorepo` at
`7c9bcc5` and fetched `origin/master` at 00:47Z — 0 ahead, 0 behind, clean. It read the
standing briefing, which named the invited-visitor arm split as the build to do "if
something must be built", and built it: migration 024 adding `visitor_events.arm`, an
FNV-1a arm derived from the visitor id, a per-arm admin read, 18 new frontend tests, 10
new backend tests, four funnel e2e tests green against real Chromium and real Postgres.
At 08:46Z it committed. At 08:47Z `git push` was **rejected**. `22a112e`, pushed at
02:56Z by a different session, was the same feature: same migration number, same column
name, same nullable-arrival-only design, the same FNV-1a hash, the same default-off
knob. Two independent readings of one briefing paragraph, converging on nearly the same
code.

**Why no vault lease would have helped, which is what makes this a distinct need.** The
2026-07-24 sighting above is about two writers racing on the vault. This was not that.
Neither pass wrote to the vault while building — the vault was only ever touched at the
end, and git would have serialised them cleanly if it had come to that. The collision was
in the **product repo**, and the thing that collided was not a write, it was the
*decision about what to work on*. Both passes read a briefing that names work and has no
way to say the work has been taken. Nothing was corrupted. Roughly eight hours of compute
produced a commit that had to be deleted.

**What actually caught it.** `git push --ff-only`, at the very end, by accident. That is
the only detector in the system, it fires after all the cost has been paid, and it only
fires at all because the two passes happened to touch overlapping files. Two passes
building *non*-overlapping duplicates of the same intent would both have pushed cleanly
and neither would ever have known.

**What was salvageable, honestly:** one 4-assertion test file the other implementation
did not have (`4906fd4`). Everything else was discarded in favour of the version already
on `master`, which was the better of the two in at least one respect — it reports
pre-experiment rows as `unassigned` rather than omitting them.

**Cost, measured rather than estimated:** one full build pass. The evidence rung stays
`observed` — this is a fact about this building's own operation, not a customer's words,
and it is another instance of the hole [[A Context node type for evidence that is true, useful, and not a customer need]] describes.

## Issues
- 2026-07-26 undefined
- 2026-07-26 **Hygiene — a destroyed annotation, flagged not repaired (2026-07-26).** One or more lines in this node read `- <date> undefined`. That is not a note anybody wrote: `ost_annotate` was called with `note` instead of its declared `issue` field, nothing validated the call, and the literal string "undefined" was appended in place of the content. The original text was never written anywhere and is unrecoverable. Fourteen such lines exist across the two live vaults, written by several passes over three days. The cause is closed in ost-agent v0.17.0, which refuses a tool call that does not match the schema the tool itself declares. **Left in place deliberately:** this vault is append-only, and rewriting history to hide a bad write is exactly the action this product refuses — including when the product is the one that made it. Full account: [[A tool call I got slightly wrong destroyed the note I was filing]].
