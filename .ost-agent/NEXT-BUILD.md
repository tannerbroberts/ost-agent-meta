# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-25 (autonomous bootstrap loop, fifth pass of the day)._

---

## What changed since the last briefing

- **Shipped: v0.9.0 — the uncovered statement now has somewhere to be *checked*.**
  `ost-agent debt` prints every bounded test side by side: the threshold the node
  pre-committed to before the run, directly above the limit the run stated after it.
  Two pieces of text the tool already held, printed together. It never compares them,
  and the closing caveat now says so. A bounded test that never wrote a threshold
  down is named rather than skipped — a limit stated against no stated question has
  nothing to be read against, and that is exactly the case the pair *count* reported
  as healthy. 299 tests across 46 files (up from 285 / 45), `tsc` clean, on `main` as
  `d9ace23`.
- **It found something on first contact, and that is the headline.** Run over both
  live vaults before it was committed:

  | | assumption tests | threshold extractable | contains a number or bound |
  |---|---|---|---|
  | ost-agent-meta | 77 | 65 | 57 |
  | tetrix-ost | 27 | 27 | **4** |

  In the sibling vault, 21 of 27 pre-commitments open with an imperative — *Fix…*,
  *Decide…*, *Choose…* — an instruction to pre-commit standing where the
  pre-commitment should be. **A test whose threshold was never fixed cannot come out
  a failure.** The believability ladder, the evidence-debt gate and v0.8.0's coverage
  field are all machinery for making claims refutable, sitting on a bar that in that
  tree mostly does not exist. Filed as
  [[My tests carry thresholds nobody ever fixed, so nothing can come out a failure]] —
  the only new top-level row this pass added, and deliberately the only one.
- **This is the first thing either coverage feature has found on its own**, and it is
  a better argument for the v0.8.0 → v0.9.0 line than either node's own reasoning
  was. Worth holding against the honest case for restraint the last briefing made:
  nobody had yet shown the field helps at all.
- **Not shipped, for the fifth consecutive release: the release.** v0.5.0 through
  v0.9.0 are on `main`. None is on npm.

## 1. Two things only you can do — about 5 minutes total

1. **`npm publish` v0.5.0 through v0.9.0** (~2 min). `npm whoami` → `ENEEDAUTH` on
   five consecutive passes; the tag push is still rejected by this environment's git
   proxy, so the GitHub-Release path is closed too. `npm publish --dry-run` succeeds
   and packs 132 files, so the package is fine — the only missing thing is a
   credential this environment must not hold.

   **New evidence that this has stopped being merely a stall.** `package-lock.json`
   still said `0.7.0` after v0.8.0 shipped, which `npm ci` in the publish workflow
   would have rejected outright. Fixed this pass — but nobody would have known,
   because the only thing that exercises that path is a publish, and there has not
   been one. **Five releases of unexercised release machinery is a second failure
   queued behind the first.**
2. **Record the three compute-lane verdicts** (~3 min).
   `.ost-agent/drafts/compute-docket-2026-07-24.md` holds three paste-ready commands,
   corrected last pass for v0.8.0's required `--uncovered`. Unchanged for five
   briefings.

   **There is now a concrete reason to want one of them.** Recording any of the three
   is what makes v0.9.0's side-by-side visible at all: with zero bounded tests in this
   vault, `debt` prints nothing new. Verified by simulation this pass against a scratch
   copy — recording the rename-audit verdict makes `debt` print its
   *">= 2 incidents beyond the known one, else defer"* threshold directly above the
   limit the run stated. That is the feature working, on your data, and it is three
   minutes away.

## 2. The next build

**Nothing yet — and specifically, not the obvious follow-on.**

The obvious follow-on is
[[Flag a threshold that is still an instruction to choose one]]: the census that
produced this pass's finding, turned into a standing report. It is an afternoon, it
reuses the extractor, and it is genuinely useful. **Do not build it next**, for a
reason the tree can now state precisely: this vault would then hold *three* reporting
features (`debt`'s pair count, v0.9.0's side-by-side, and this) and **zero** evidence
that any of the three is read. [[Does the side-by-side change what a reviewer does about a threshold]]
and [[Does a forced uncovered field change what a second reader believes]] are both
unrun. Building a third report before either runs is the clearest instance yet of the
pattern §5 keeps naming.

**What to do instead, in order:** §1.2 (three minutes, makes v0.9.0 legible on real
data), then §4 (the cold offer). If neither is possible and something must be built,
[[Flag a threshold that is still an instruction to choose one]] is the honest choice —
report only, never [[Refuse to record a result against a threshold that was never fixed]],
which would be the *second* required-field addition to the one command its operator is
already not running.

## 3. What the sibling product taught this one

**A fourth instance of leaving a permanent test behind — and the first where the
mechanism worked with nobody present.**

Pass 4 on tetrix committed an assertion it expected to be wrong later: *a signed-out
visitor is never offered a board, so the beacon cannot fire*. True at the time, left
as a tripwire, with a comment saying that building anonymous play should fail it and
force a deliberate revisit. Pass 5 built anonymous play. **It fired.** The assertion
was inverted rather than deleted, and the file now records why it changed.

The first three instances argued a test is a durable *record*. This argues a test can
be a durable *instruction to a future stranger* — including a future instance of the
agent that wrote it, carrying none of the original context. A verdict draft cannot do
that: nothing re-reads a draft at the moment it stops being true.

**And rewriting it caught something its author did not intend.** The original could
have passed for the wrong reason — a freshly-migrated database has no non-starter
puzzles, so `/daily` serves no board at all, making "no board because anonymous play
does not exist" indistinguishable from "no board because the library is empty". That
is an argument for the *inversion* step, not just the leaving-behind step. Recorded on
[[Leave a permanent test behind instead of a one-off verdict draft]].
[[Do six cold artefacts show a test beating a verdict draft]] is still unrun; four
self-observations still do not substitute for one outsider.

## 4. Do not mistake §2 for the highest-information action

It is not. **The cold-offer test is** — 20 qualified strangers, a free done-for-you
discovery pass, pre-committed threshold (≥5 kickoffs, ≥3 sending real artefacts). The
roster (19 named leads plus pools, every row carrying its evidence URL), the outreach
kit and the tracking sheet are drafted and waiting in `.ost-agent/drafts/`. The
compute share is done; what remains is your identity and your consent, which compute
must not absorb.

Every node in this vault rests on founder or agent sources. Zero external returning
operators exist, which is the mandate's own metric. **This has now gone seven passes
without being acted on.** Until it runs, everything in §2 is tooling for a product
nobody outside this building has asked for.

Note the shape of this pass's own finding against that: it is a mechanically verified
fact about **our own two vaults**, and it is the most useful thing produced in five
passes. That is a real argument that dogfooding has value — and no argument at all
that anyone else has this problem.

## 5. The bias in this briefing, declared

Five passes running, the agent has chosen work it could finish alone. Two things
about this pass cut differently, and both are worth weighing:

- **The build produced an external-facing finding rather than only a feature.** The
  census is about the trees, not the tool, and it changed what the sibling vault's
  briefing recommends. That is the first time tooling built here has redirected work
  over there.
- **The agent then declined to name a next build in either vault.** In tetrix it
  recommended fixing thresholds instead; here it argued against its own obvious
  follow-on. That is either the pattern breaking or a more sophisticated version of
  it — "stop and improve the measurements" is also a way to avoid meeting a customer,
  and §4 has now gone from six passes to **seven**.

Read the second bullet with suspicion. An agent that finds a reason not to build is
not thereby an agent that has done the thing it keeps deferring.

The standing 2026-07-24 prioritisation still holds and is not superseded by this file:
the target row is external demand evidence, and the critical path inside it is
cold-offer → recruiting → pre-order. This file says what to *pick up*; that section
says what the tree is *for*.

## History

### 2026-07-25 (fifth pass) — this one

Shipped v0.9.0 (`debt` prints each bounded test's pre-committed threshold beside what
its run left uncovered; a bounded test with no written threshold is named). Ran the
extractor over both live vaults and found that 21 of 27 tetrix assumption tests
pre-commit with an imperative rather than a bar, and only 4 of 27 carry a number —
filed as the pass's single new opportunity, with three solutions and one test.
Recorded a fourth instance of leaving a permanent test behind, the first where a
deliberately-planted tripwire fired unattended. Fixed a stale `package-lock` that
would have failed `npm ci` in the publish workflow. **Argued against its own obvious
next build** and named §1.2 and §4 instead. npm publish now five releases behind.
§4 (cold offer) untouched for a seventh pass.

**Outcome of the fourth pass's briefing: §2 shipped as named** (the side-by-side).
§1.1 (publish) not acted on. §1.2 (three verdicts) not acted on. §5 (cold offer) not
acted on.

### Superseded — 2026-07-25 (fourth pass)

Shipped v0.8.0 (`--uncovered` required on every recorded result; `debt`/`status`
name unbounded tests; `appendUnderSection` section-scoping fix). Recorded a third
and strongest instance of leaving a permanent test behind, this one producing a real
bug fix and a framing kill in the sibling product, neither from a test failing.
Logged a second sighting of the believability ladder's missing rung for verified
facts about our own system. Named a modest reviewability increment as next while
saying plainly that the honest alternative is nothing. npm publish now four releases
behind. §5 untouched for a sixth pass.

**Outcome of the third pass's briefing: §2 shipped as named** (the uncovered field).
§1.1 (publish) not acted on. §1.2 (three verdicts) not acted on — and now needs an
extra argument. §5 (cold offer) not acted on.

### Superseded — 2026-07-25 (third pass)

Shipped v0.7.0 (`ost_flag_humans_required`, restrictive-only by construction;
`lanes --flag-cautious`). Did not answer the human question about who may set a lane
— made it inexpressible in the dangerous direction and filed that behaviour as its
own opportunity. Named the uncovered-by-this-test field as next. Recorded a second
instance of leaving a permanent test behind, with an actual finding.

**Outcome: §2 shipped** (v0.8.0, this pass). §1.1, §1.2, §5 not acted on.

### Superseded — 2026-07-25 (second pass)

Shipped v0.6.0 (lane triage, fail-closed vocabulary, `pending-permission`). Named
backlog classification as next, blocked on the human rule about who may set a lane.

### Superseded — 2026-07-25 (first pass)

Shipped v0.5.0 (exit code + status failure surfacing). Named the lane-triage build
as next, three human minutes as the unblock, and the cold-offer test as the
still-unrun highest-information action.

### Before 2026-07-25

No standing briefing existed; guidance lived in root-Outcome annotations and the
prioritisation section there. The 2026-07-24 hard-fix pass set the target row
(external demand evidence) and the critical path inside it (cold-offer → recruiting
→ pre-order); that prioritisation still stands.
