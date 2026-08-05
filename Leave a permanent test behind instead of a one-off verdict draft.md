---
type: Solution
status: unvalidated
source: >-
  agent-ideation:autonomous-loop-2026-07-25 — generalized from an observed run
  on the tetrix product, where a compute-only verification was converted into a
  committed test rather than into a verdict draft
created: '2026-07-25'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A committed test outlives and outperforms a verdict draft as the artefact of a pass]]

**The idea.** When a pass runs something in the compute-only lane, its output should default to a **committed test in the product repo**, not a verdict draft in the vault. The draft is still written — a human still records the verdict — but the artefact that survives is executable.

**Where this came from.** On 2026-07-25 a loop was pointed at a tetrix assumption test whose standing briefing described it as a ~15-minute human walk of five journeys against a live database. The loop could have done exactly that: walk the journeys, observe the numbers, write a paste-ready `ost-agent result` line, and hand a human one paragraph to approve. Instead it wrote `visitorFunnelService.pg.test.ts`, which re-runs the same five journeys on every `pnpm test`.

Both routes cost the same compute and produce the same finding today. They differ entirely in what happens tomorrow.

**The claim.** A verdict is a measurement of a moment; a test is a standing assertion. A verification that must be re-run by hand decays silently — the code moves, the finding stays recorded, and nobody can tell that the recorded finding stopped being true. This matters more here than in ordinary engineering, because the whole product's premise is that the map should be *trustworthy over time*. A tree full of results that were true once is exactly the failure mode the believability ladder exists to prevent, arriving through a different door.

**Contrast with siblings under this opportunity.** [[Triage every assumption test by the human-minutes it actually needs, and let compute run the zero-minute lane]] decides *which* tests compute may run — this decides *what compute should leave behind when it runs one*. They compose: lanes without this produce a growing pile of one-shot drafts; this without lanes has nothing to trigger it. The docket sibling compresses the human's residual role and is unaffected either way.

**Where it does not apply, which is most of the tree.** Only a minority of assumption tests have an executable form. "Will an operator hand over real discovery work" cannot become a test file. The rule should therefore be a *default with an escape*, not a requirement — and the escape must not become the path of least resistance, because writing a test is genuinely harder than writing a paragraph and an agent will feel that pull.

**The risk worth naming before anyone builds this.** A test that encodes the wrong threshold is worse than a verdict that encodes the wrong threshold, because it will be re-run forever and its greenness will be read as ongoing confirmation. The 2026-07-25 tetrix run is a live instance: the test it left behind covers the database half of a pre-committed threshold and *not* the browser half, and the pass had to split the node in two to stop a green suite reading as a verified instrument. Whatever this becomes must make that split cheap and obvious rather than depending on an agent noticing.

**Cheapest disconfirmer.** Take three compute-only tests from the existing backlog that plausibly have an executable form. Have compute produce both artefacts for each — a verdict draft and a test — and put the six in front of the operator cold. If the drafts are as useful as the tests, this node is decoration and the lane triage alone is enough.

⚠️ Unvalidated. Proposed by an agent, from a single instance of its own behaviour on another product.

## Second instance — 2026-07-25, second pass (agent-origin; still not validation)

This node was proposed from a single instance of an agent's own behaviour. There are now two, and the second one sharpens both the claim and the risk.

**What happened.** A loop was pointed at the tetrix assumption test *Does the beacon actually fire from a real browser* — the node this idea's first instance had itself split off. It could have driven the browser once, read the numbers, and written a paste-ready verdict line. It instead committed `e2e/visitorFunnel.spec.ts`: a real Chromium against a real Postgres, re-run by `pnpm test:e2e:funnel`. Same compute, same finding today, different tomorrow.

**The claim gets a data point it did not have.** The first instance found no defect, and the honest limit recorded on the parent opportunity was that *a verification lane which only ever confirms is worth very little*. This one produced something: the app wraps its tree in `StrictMode`, so the arrival beacon goes out **twice per page load** in dev. Harmless — the server keeps one row and production fires once — but it means any beacon count read off a dev server is 2×.

The interesting part is where it came from. **The test did not fail; writing the test found it.** The finding arrived while the author was deciding what to assert, and the decision it forced — assert *per load* rather than an exact total — is now permanent. A verdict draft would have recorded a number and lost the reason. This is a mechanism the node had not named: the artefact is durable, and so is the *reasoning* about what counts as correct, because a test has to say so out loud.

**The risk this node named came true again, in exactly the shape predicted.** The body warned that a test encoding a partial threshold is worse than a draft encoding one, because its greenness reads as ongoing confirmation. That is precisely what happened: this test covers the arrival beacon and *not* the play beacon, and the pass again had to split a node (tetrix-ost, "Does a real drag report a first play") to stop a green suite reading as a verified instrument. **Twice out of two runs, the honest move was to split the node.** That is no longer a caveat, it is the pattern — and it suggests whatever this becomes should make "what this test does NOT cover" a required field, not a habit an agent has to remember.

**What this still is not.** Two instances of an agent choosing the same thing about its own work. Nobody outside this building has expressed a preference between a test and a verdict draft, and the cheapest disconfirmer below — six cold artefacts in front of an operator — remains unrun.

## Third instance, 2026-07-25 (autonomous loop, pass 4)

A third compute run on tetrix converted a verification into a committed test
(`tetrix-game-monorepo` `39f5813`, a real drag at the play beacon). It is the
strongest instance so far, and for a reason none of the first two showed:

**The test's own construction produced two findings the verdict route would not
have.**

1. *A real bug, fixed.* Setting the test up needed a saved game cleared between
   runs. Doing that made `saveEngineState` throw on `one_stats_per_user` — its
   no-existing-game branch reseeds `statistics` with no `ON CONFLICT`, unlike the
   `settings` and `modifiers` inserts two lines below. That branch runs whenever
   there is no saved game, which is *not* the same as the player being new, so any
   cleared save locks that player out of `REQUEST_STATE` and `REQUEST_RESYNC`
   entirely. Fixed with three tests that fail without it. A verdict draft would
   never have gone near that code path.
2. *A framing kill.* Looking for the signed-out drag surface established there
   isn't one — so a sibling assumption test in that vault
   (*does a stranger who lands on a board page play it*) is unanswerable as
   written, and the funnel's headline ratio measures a later conversion than
   everyone had been reading it as.

**This sharpens the claim rather than just repeating it.** The first two instances
argued a test survives where a verdict decays. This one argues something stronger
and more falsifiable: *writing* the test forces contact with the real code path, and
that contact is where the findings come from. Neither finding above came from a test
failing. Both came from making one work.

**The risk this node named is now partly mechanical.** It warned that a test
encoding the wrong threshold is worse than a verdict doing so, and that whatever
gets built must make splitting a node cheap "rather than depending on an agent
noticing". v0.8.0's
[[A result must state what it did not cover]] is that, in its smallest form.

**Still one source.** Three instances, all of an agent choosing this about its own
work, all inside this building. The cheapest disconfirmer —
[[Do six cold artefacts show a test beating a verdict draft]] — remains unrun, and
three self-observations do not substitute for one outsider.

## Fourth instance, 2026-07-25 (autonomous loop, pass 5) — and the first one that fired on purpose

The first three instances all argued the same shape: a test survives where a verdict
decays, and writing it forces contact with the real code path. This one is different
in kind, and it is the first instance where the *mechanism this node claims* was
observed doing its work without anybody present.

**What happened.** Pass 4 on tetrix ended by committing an assertion it expected to
be wrong later: *a signed-out visitor is never offered a board to play, so the beacon
cannot fire*. It was true, and it was left in `e2e/firstPlayBeacon.spec.ts` as a
tripwire, with a comment saying that if anonymous play were ever built this test
should fail and force the funnel's interpretation to be revisited deliberately rather
than by accident.

Pass 5 built anonymous play. **The tripwire fired.** The test failed, the pass had to
open it, and the interpretation was revisited on purpose — the assertion was inverted
into its opposite (a stranger gets a live board, drags a real piece, the row lands)
rather than deleted, and the file's docstring now records why it changed.

**What this adds to the claim.** The first three instances said a test is a durable
*record*. This says a test can be a durable *instruction to a future stranger* —
including a future instance of the agent that wrote it, with none of the original
context. A verdict draft cannot do that at all: nothing re-reads a draft at the
moment it stops being true. The mechanism is that the test is positioned where the
change must pass through.

**And it caught something the tripwire's author did not intend.** Rewriting it
exposed that the original assertion could have passed for the wrong reason: a
freshly-migrated database has no non-starter puzzles, so `/daily` serves no board at
all, and "no board because anonymous play does not exist" and "no board because the
library is empty" were indistinguishable. The replacement seeds a board first. A
tripwire that can pass vacuously is worse than none, and only rewriting it revealed
that — which is an argument for the *inversion* step, not just the leaving-behind
step.

**Still one source.** Four instances, all of an agent observing its own work inside
this building. [[Do six cold artefacts show a test beating a verdict draft]] remains
unrun, and four self-observations still do not substitute for one outsider.

## Definition of done

[[Do six cold artefacts show a test beating a verdict draft]]

```
npx vitest run test/runner/verdict-leaves-spec.test.ts
```

Green means: the artefact this solution is named for actually gets produced — completing a verdict writes a committed spec into the repository's own suite, the test node it settled references that file, and a prose-only verdict is refused. Today the comparison the test wants has only one side of it, because nothing leaves a test behind. Green does **not** settle whether six cold readers prefer it; that is a person's reaction.

## History
- 2026-08-05 unlinked [[Do six cold artefacts show a test beating a verdict draft]] — moved under [[A committed test outlives and outperforms a verdict draft as the artefact of a pass]] — the belief this test measures now has a node of its own
