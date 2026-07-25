# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-25 (autonomous bootstrap loop, second pass of the day)._

---

## What changed since the last briefing

- **Shipped: v0.6.0 — lane triage**, the build the last briefing named. Every
  `AssumptionTest` can carry a `lane` (`compute-only` / `one-command` /
  `pending-permission` / `humans-required`); `ost-agent lanes` groups the tree by what
  each test costs a person; `ost-agent lane … --set --by --why` classifies one,
  attributed and recorded in History. 243 tests green across 42 files, `tsc` clean.
- **The safety trade-off was answered structurally, not carefully.** The vocabulary
  fails closed (exactly one lane is compute-runnable; unclassified, unknown, and
  future-invented lanes all answer *no*), a garbage lane is dropped at deserialization,
  and the triage aid can only ever point at `humans-required`. Care is not a mechanism;
  these are.
- **`pending-permission` shipped as a real lane** — folded in from last pass's observed
  stall, exactly as the briefing asked. An opportunity note from one pass became a type
  in the next pass's code, which is the loop working as intended.
- **Learned, from the *other* product:** compute ran a verification lane end to end on
  tetrix — a task a previous pass had classified as a 15-minute human job. It was not.
  See §3; it changes what lanes are *for*.
- **Not shipped, for the second consecutive release: the release.** v0.5.0 *and* v0.6.0
  are on `main` and neither is on npm.

## 1. Three things only you can do — about 9 minutes total

Ordered by what unblocks the most. None is a build.

1. **`npm publish` v0.5.0 and v0.6.0** (~2 min). Two releases now sit unpublished
   behind one credential. `npm whoami` → `ENEEDAUTH` on both passes, and the tag push
   was rejected by this environment's git proxy on both passes, so the
   GitHub-Release-fires-the-workflow path is also closed. This is no longer a stall,
   it is a backlog that grows every pass and gets less reviewable as it does. Until it
   runs, `npx -y ost-agent@latest mcp` — the plugin's own install path — describes a
   package that does not exist at these versions.
2. **Rule on who may set a lane** (~3 min). This is the decision that gates the
   remaining half of the feature you just got. If the agent may label a test
   `compute-only`, the agent can authorize itself to run it and all three safety
   mechanisms become decoration — so the lane surface shipped CLI-only, like
   `ost-agent result`. A concrete middle exists and the agent recommends it while
   flagging its own interest: **let the agent set `humans-required` freely (it only ever
   restricts compute) and reserve every permissive lane for a human.** That is
   `suggestCaution`'s rule, promoted from advice to permission.
3. **Record the three compute-lane verdicts** (~4 min).
   `.ost-agent/drafts/compute-docket-2026-07-24.md` still holds three paste-ready
   `ost-agent result` commands — one SUPPORTED and two kills. Unchanged from last
   briefing and still true: this vault has never recorded an evidence-driven kill, and
   two are sitting there ready. v0.6.0 now *also* stands on the unrecorded one.

## 2. The next build

**Classify the existing test backlog, under whatever rule §1.2 sets.**

The model shipped; the tree is still entirely unclassified, which by the fail-closed
rule means **zero tests are runnable by compute today**. The feature currently buys
nothing until the backlog is labelled. That is the correct default and also a real gap.

Smallest useful version, once the rule exists: run `ost-agent lanes`, let
`suggestCaution` flag the tests naming outside people, apply `humans-required` to those
in bulk, and leave everything else unclassified for a human to promote. Even that
partial pass is worth having — it makes the permissive set small and explicit instead
of large and unexamined.

**Do not let the loop classify permissively on its own initiative before §1.2 is
answered.** The agent wrote the rule that stops it doing this; it should not be the one
to relax it.

## 3. The finding worth more than the feature

A previous pass wrote, in the tetrix briefing, that verifying the funnel instrument was
a ~15-minute human task. This pass did it with no human: no Docker daemon, so it found
PostgreSQL 16 binaries on the box, initialised a cluster, applied 23 migrations, and
turned the five-journey hand-walk into a committed test — 16 checks, green, re-run on
every commit.

**Two things follow, and the second is the one that should change a decision.**

- A previous pass's lane classification was wrong in the safe direction. That is the
  system working, and it is also a warning: human-minutes estimates written by an agent
  are guesses, and the backlog in §2 will be full of them.
- **The saving was never the fifteen minutes.** A hand-walk verifies one afternoon; a
  test verifies every commit forever. The lane triage's real product may be *converting
  expiring human verification into non-expiring mechanical verification* — which is a
  different claim from "compute is cheaper than you", and a better one. New candidate
  filed under the compute-only opportunity: [[Leave a permanent test behind instead of a
  one-off verdict draft]], with its cheapest disconfirmer as
  [[Do six cold artefacts show a test beating a verdict draft]].

Its honest limit is recorded on the opportunity too: the run found no defect, so it
produced no news. A verification lane that only ever confirms is worth very little. The
case that matters — compute finds something and a human must decide what it means — has
not happened yet.

## 4. Do not mistake §2 for the highest-information action

It is not. **The cold-offer test is** — 20 qualified strangers, a free done-for-you
discovery pass, pre-committed threshold (≥5 kickoffs, ≥3 sending real artefacts). The
roster (19 named leads plus pools, every row carrying its evidence URL), the outreach
kit, and the tracking sheet are drafted and waiting in `.ost-agent/drafts/`. The compute
share is done; what remains is your identity and your consent, which compute must not
absorb.

Every node in this vault rests on founder or agent sources. Zero external returning
operators exist — the mandate's own metric. **This has now gone four passes without
being acted on.** Until it runs, everything in §2 is tooling for a product nobody
outside this building has asked for.

## 5. The bias in this briefing, declared

Last pass shipped an internal correctness fix and recommended internal tooling. This
pass built that tooling and is now recommending applying it to the backlog. Two passes
running, the agent has chosen work it can complete alone and deferred the work that
needs another person — and §4's counter has gone from three passes to four.

The one thing that partly redeems this pass is §3, which was not planned: the useful
finding came from being *wrong* about a lane, not from building the lane feature. That
is the shape of evidence worth optimizing for, and it is not the shape of §2.

---

## History

### 2026-07-25 (second pass) — this one

Shipped v0.6.0 (lane triage, fail-closed vocabulary, `pending-permission`). Named
backlog classification as next, blocked on the human rule about who may set a lane.
Recorded that a previous pass's human-minutes estimate was wrong in the safe direction,
and filed the leave-a-test-behind candidate from it. npm publish now two releases
behind. §4 untouched for a fourth pass.

### 2026-07-25 (first pass)

Shipped v0.5.0 (exit code + status failure surfacing). Named the lane-triage build as
next, three human minutes as the unblock, and the cold-offer test as the still-unrun
highest-information action.

**Outcome: §2 acted on and shipped** (v0.6.0, this pass). §1.1 not acted on — publish
still pending. §1.2 not acted on — the three verdicts are still unrecorded. §1.3 not
acted on — the market-scan gate is still unruled. §3 not acted on.

### Before 2026-07-25

No standing briefing existed; guidance lived in root-Outcome annotations and the
prioritisation section there. The 2026-07-24 hard-fix pass set the target row (external
demand evidence) and the critical path inside it (cold-offer → recruiting → pre-order);
that prioritisation still stands and is not superseded by this file — this file says what
to *pick up*, that section says what the tree is *for*.
