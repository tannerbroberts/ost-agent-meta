---
type: Opportunity
status: unvalidated
source: 'INBOX:2026-07-24-friction-two-loops-share-one-git-managed-vault-with-no-wr.md'
created: '2026-07-25'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[A merge conflict got committed into a source file, so the next run inherits a repo that cannot build]]
[[Two runs write the same vault at once and nothing arbitrates between them]]
[[A second pass builds what the first already built, because nothing says the work was taken]]

**The need (operator's voice):** "I had a thinker loop and a builder loop working the same git vault. Nothing told either whose turn it was — the builder had to check for a clean tree and hope, and would have had to back off mid-work if the thinker were mid-commit."

**Why it matters:** unattended operation (the parent need) assumes the processes writing the vault coordinate. There is no lease, no queue, no write contract — so adding a second loop converts 'walk away safely' into 'walk away and hope the writers interleave kindly'. Observed at the moment of friction by the builder loop, 2026-07-24.

**Litmus (more than one way?):** yes — a lock/lease file, a write queue, single-writer-per-vault convention, or serializing loops through one scheduler are all distinct answers.

**Solution ideation deferred:** dogfood-lane need; expand when prioritized (see root Prioritization).

## History
- 2026-07-24 evidence: (none) → observed — labeled at creation intent; ost_create_node@0.1.3 silently dropped the evidence input
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.
- 2026-08-05 unlinked "One writer at a time, enforced by a lock the second agent waits on rather than ignores" — re-parented under "Two runs write the same vault at once and nothing arbitrates between them" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Each agent writes on its own branch, and merging is a deliberate, reviewable step" — re-parented under "Two runs write the same vault at once and nothing arbitrates between them" — this solution answers that need, not the categories beside it
- 2026-08-05 unlinked "Detect drift at write time and refuse, naming what changed since the read" — re-parented under "Two runs write the same vault at once and nothing arbitrates between them" — this solution answers that need, not the categories beside it

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
and it is another instance of the hole "A Context node type for evidence that is true, useful, and not a customer need" describes.

## Issues
- 2026-07-26 undefined
- 2026-07-26 **Hygiene — a destroyed annotation, flagged not repaired (2026-07-26).** One or more lines in this node read `- <date> undefined`. That is not a note anybody wrote: `ost_annotate` was called with `note` instead of its declared `issue` field, nothing validated the call, and the literal string "undefined" was appended in place of the content. The original text was never written anywhere and is unrecoverable. Fourteen such lines exist across the two live vaults, written by several passes over three days. The cause is closed in ost-agent v0.17.0, which refuses a tool call that does not match the schema the tool itself declares. **Left in place deliberately:** this vault is append-only, and rewriting history to hide a bad write is exactly the action this product refuses — including when the product is the one that made it. Full account: "A tool call I got slightly wrong destroyed the note I was filing".

## Corroboration — caught in the act, twice (unattended sweep, 2026-08-03)

Two of twenty-two sessions read this pass recorded a concurrent writer directly, rather than as a worry.

**Session `424486ec` (2026-07-30) names it in the agent's own words.** After two failed edits, the agent stopped and asked: *"Another process is writing to this repo right now (HEAD moved to the PR #22 merge, and ~14 source files have uncommitted changes touched seconds ago, including a brand-new `pushTargetFor` that …"*. Every element this node predicts is present — a second writer, a moved HEAD, fourteen files changed within seconds, and an agent that could only detect it forensically, by noticing that its own assumptions had stopped holding.

**Session `06eba571` (2026-07-26) shows the state that leaves behind.** Its single friction event is a `git` fetch returning exit 128: *"You have divergent branches and need to specify how to reconcile them."* Two lines of history from two writers, and no rule on hand for whose wins.

The distinction worth preserving: this node is about the *damage to shared state*, and "The file changed after I read it, and the failed edit is how I find out" is about the *damage to a single call issued against an expired read*. `424486ec` is the session where both happened at once — the failed edits were the symptom, the second writer was the cause — which is why it appears in both places.

_Source: `TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab` and `TRANSCRIPT:06eba571-9780-458a-b384-da5abe101e6f` — observed behavior from the agent's own transcripts. Grounds usability, not demand. Note that both concern the source repository rather than a vault; whether that generalises to two agents on one vault is an inference a human should rule on, not a fact these records establish._

## Observed corroboration — 2026-08-05 sweep

`TRANSCRIPT:424486ec-3489-4b53-8e2b-012232d221ab` caught this happening rather than being predicted. In one session the agent hit two `Edit` failures reading `String to replace not found in file`, then stopped and asked the operator to confirm what it had inferred: another process was writing to the repo at that moment — HEAD had moved to a merge commit, roughly fourteen source files carried uncommitted changes touched seconds earlier, and a symbol existed that had not existed when the file was read.

Two things in that sequence are worth keeping. First, the collision announced itself only as a *failed edit* — the same error text a stale read produces when nobody else is involved, which is why the agent needed a second signal (the git state) to tell the two apart at all. Second, the agent could not resolve it alone and spent a clarifying question on it, so a concurrent writer converted an unattended run into a blocked one. That links this opportunity to "The whole loop waits on one human command, and nobody is told it is waiting" without either being a duplicate of the other: this is the cause, that is the cost.

Observed behavior from the agent's own session, so it grounds usability and the collision's existence — not how often two *operators* would collide, which is still unmeasured.
