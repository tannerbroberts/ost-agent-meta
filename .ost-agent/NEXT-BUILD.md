# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-25 (autonomous bootstrap loop, fourth pass of the day)._

---

## What changed since the last briefing

- **Shipped: v0.8.0 — a result must say what it does *not* cover.**
  `ost-agent result` now requires `--uncovered` alongside `--by`, and refuses a
  blank one. Same argument in both cases: an unattributed result cannot be told
  apart from a fabricated one, and an **unbounded** one cannot be told apart from a
  complete one. Each recording appends a line to `## Results` and a line to
  `## Uncovered`, in that order, so a second run cannot ride on the first run's
  limits; `debt` and `status` count the pair and name the mismatches. 285 tests
  across 45 files (up from 265 / 44), `tsc` clean, on `main` as `d9ed3ac`.
- **A real bug came with it.** `appendUnderSection` was appending to the end of the
  node *body* rather than the end of the named *section*. Invisible while nodes had
  one growing section; wrong the moment they had two — a status change recorded
  after a result would have filed itself under `## Results`. The new feature is what
  exposed it, which is itself a small instance of §4.
- **Older vaults stay readable.** A result recorded before the field existed, or a
  node a human hand-flipped to `validated` with nothing written down, reads as one
  unbounded claim rather than as an error. Debt surfaced, not enforced backwards.
- **Not shipped, for the fourth consecutive release: the release.** v0.5.0 through
  v0.8.0 are on `main`. None is on npm.

## 1. Two things only you can do — about 5 minutes total

1. **`npm publish` v0.5.0, v0.6.0, v0.7.0 and v0.8.0** (~2 min). `npm whoami` →
   `ENEEDAUTH` on four consecutive passes, and the tag push was rejected by this
   environment's git proxy again, so the GitHub-Release-fires-the-workflow path is
   closed as well. `npm publish --dry-run` succeeds and packs 132 files, so the
   package itself is fine — the only missing thing is a credential this environment
   must not hold. Until it runs, `npx -y ost-agent@latest mcp` — the plugin's own
   install path — describes a package that does not exist at any of these versions.
   **This is now the single longest-running blocked item in either vault**, and it
   gets less reviewable every pass: four releases of unpublished change is no longer
   a stall, it is a backlog.
2. **Record the three compute-lane verdicts** (~3 min).
   `.ost-agent/drafts/compute-docket-2026-07-24.md` still holds three paste-ready
   `ost-agent result` commands — one SUPPORTED and two kills. Unchanged for four
   briefings. **Note they now need one more argument each**: v0.8.0 requires
   `--uncovered`, so the drafted lines will be refused as written. That is the
   feature working, and it is also the first time this loop has made a human's
   waiting task *harder*; if it reads as friction rather than as a prompt, that is
   evidence against [[A result must state what it did not cover]] and should be
   said out loud.

## 2. The next build

**Give the uncovered statement somewhere to be *checked*, not just written.**

v0.8.0 checks that a sentence exists. It never reads it, and it says so. The natural
next increment is the cheapest thing that makes the sentence load-bearing:
`ost-agent debt` already knows which tests are unbounded — let it also surface, for
each *bounded* test, the uncovered line next to the threshold the node's body
pre-committed to, side by side, so a human can see in one screen whether the run
answered the question that was asked. No parsing, no judgement, no model: two pieces
of text the tool already has, printed together.

That is deliberately unambitious, and the reason is §5. The honest case for it is
that it costs an afternoon and makes the existing feature's output reviewable. The
honest case against it is that nobody has yet demonstrated the existing feature
helps at all — see the new
[[Does a forced uncovered field change what a second reader believes]], which is
unrun and which could refute the whole line.

**Second choice, and it is a real one: nothing.** §5 has now gone six passes.

## 3. What the sibling product taught this one

A third compute run on tetrix converted a verification into a committed test — and
this instance is stronger evidence than the first two, for a specific reason:
**writing the test produced two findings, neither of which came from a test
failing.**

1. A real player-facing bug, fixed: `saveEngineState` reseeds a `statistics` row
   with no `ON CONFLICT`, so any player whose saved game is cleared is locked out of
   `REQUEST_STATE` and `REQUEST_RESYNC` entirely. Found because the test needed to
   reset a saved game. A verdict draft would never have touched that path.
2. A framing kill: a signed-out visitor has no playable surface at all, so a sibling
   assumption test over there is unanswerable as written and the funnel's headline
   ratio measures a later conversion than anyone was reading it as.

Recorded on [[Leave a permanent test behind instead of a one-off verdict draft]].
The claim it sharpens is falsifiable and worth stating plainly: *writing* the test
forces contact with the real code path, and the contact is where the findings come
from. Still three self-observations from inside one building;
[[Do six cold artefacts show a test beating a verdict draft]] is still unrun.

## 4. A second sighting of the ladder's hole

The tetrix finding above is mechanically verified, twice, and load-bearing — and it
had to be filed at `assertion`, the floor, because every rung on the believability
ladder describes what a *customer* did or said. "Verified fact about our own system"
has nowhere to sit, so it lands next to founder theory and gets weighted like it.

That is a second independent sighting of
[[A Context node type for evidence that is true, useful, and not a customer need]],
from the other product, arrived at without reference to the node. Annotated there.
What makes it worth your attention: the stranded item was the single most
consequential thing that pass found, and the ladder had no way to say so.

## 5. Do not mistake §2 for the highest-information action

It is not. **The cold-offer test is** — 20 qualified strangers, a free done-for-you
discovery pass, pre-committed threshold (≥5 kickoffs, ≥3 sending real artefacts).
The roster (19 named leads plus pools, every row carrying its evidence URL), the
outreach kit and the tracking sheet are drafted and waiting in `.ost-agent/drafts/`.
The compute share is done; what remains is your identity and your consent, which
compute must not absorb.

Every node in this vault rests on founder or agent sources — 182 of 188 at
`assertion`, 6 at `observed`, none above. Zero external returning operators exist,
which is the mandate's own metric. **This has now gone six passes without being
acted on.** Until it runs, everything in §2 is tooling for a product nobody outside
this building has asked for.

## 6. The bias in this briefing, declared

Four passes running the agent has chosen work it could finish alone: a correctness
fix, internal tooling, a narrowing of its own permissions, and now a required field
on a command only humans run. Each defensible; the pattern is the finding, and §5's
counter has gone from five passes to six.

Two things are different this pass and both cut against the agent:

- **It made a human's job harder.** v0.8.0 invalidates the three paste-ready verdict
  lines that have been waiting for four briefings. An agent that keeps adding
  requirements to the one command its operator is already not running should be
  watched for exactly that.
- **The most valuable thing this pass produced was not in this product.** It was a
  bug fix in the sibling, found by accident. That is worth noticing when reading
  §2's confidence.

The standing 2026-07-24 prioritisation still holds and is not superseded by this
file: the target row is external demand evidence, and the critical path inside it is
cold-offer → recruiting → pre-order. This file says what to *pick up*; that section
says what the tree is *for*.

---

## History

### 2026-07-25 (fourth pass) — this one

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
