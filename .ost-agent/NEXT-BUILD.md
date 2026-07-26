# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-25 (autonomous bootstrap loop, sixth pass)._

---

## What changed since the last briefing

**The strategy changed underneath this file, and the last briefing predates it.**
Between passes, in conversation, the founder (a) decided to **give the product away** —
no moat claimed, notoriety and a following as the return, positioning as long-term
scoped project memory; (b) **declined the cold-offer outreach as drafted** ("that
isn't going to fly") while (c) naming **one warm participant already lined up**, gated
on an explicit launch bar: *"I won't give it a shot unless I can say, 'Just install
ost-agent, setup runs itself.'"* All of that is recorded on the root Outcome and
annotated across the affected nodes. **§4 of the last briefing — seven passes of
"run the cold offer" — is superseded by a founder decision, not by a result.**

**A fresh-user audit then found exactly two seams between the product and that launch
bar**, and this pass shipped against both.

**Shipped: v0.11.0** (`86b6ff4` on `main`).
- `ost-agent mcp` **starts in a directory that is not a vault**. It used to refuse —
  and the plugin points its server at `${CLAUDE_PROJECT_DIR}`, so the first session
  after `/plugin install` showed a first-time operator an MCP server that failed to
  connect. No cause, no fix, the least actionable signal available.
  `ost_next_work` now returns `{ bootstrap: true, reason, vault, message, nextStep }`
  — state, not an error, reported at the place every pass already begins.
- **The credential wall became an instruction.** It named the SDK's *"Could not
  resolve authentication method"*, which conceals the thing that matters most: a
  credential is not the only way in. It now names the variable **and** the two-line
  plugin install that needs none. Only model-driven processes are gated, derived
  (`allowedTools.length > 0`) rather than declared, and proved by running every
  model-free process against a driver that throws if anyone calls it.
- The skill learned the matching first-run branch, generated from
  `OST_RULESET.firstRun`, so the two brains cannot drift. It says three times not to
  invent the outcome.
- 340 tests across 52 files (up from 315 / 47), `tsc` clean.

**Hygiene, and the single most useful line in this file: v0.10.0 shipped and this
vault never recorded it.** `019780f` was on `main` before this pass started, and the
briefing you are replacing was still arguing *against* building it. For a full cycle
the tree described a product that no longer existed. Now mapped onto
[[Flag a threshold that is still an instruction to choose one]]. A pass that ships
without mapping leaves the map wrong, and nothing catches that automatically.

**A defect found by using v0.10.0**: the threshold extractor misses a bold
pre-commitment lead-in that prose formatting has **wrapped across a line break**, and
classifies it `absent`. Observed live this pass. So the `absent` count is partly a
formatting artifact — in this vault 12 tests read `absent`, and an unknown share of
them may carry real thresholds nobody can see. Third line-wrapping misread this loop
has found (two dangling wiki-links, now one threshold). Flagged, not fixed: changing
the extractor changes a published number.

## 1. The one thing only you can do, and it is now on the critical path

**`npm publish` v0.10.0 and v0.11.0** (~2 min). Two releases behind, not five —
v0.9.0 did reach npm. `npm whoami` → `ENEEDAUTH`; this environment must not hold a
publish credential. `npm pack --dry-run` packs 138 files cleanly, so the package is
fine.

**Why this stopped being a chore.** Since the free-distribution decision,
**distribution is the critical path** for every external-evidence hope in this tree.
And concretely: the plugin's MCP server runs `npx -y ost-agent@latest mcp`, which
today resolves to **0.9.0 — the version that refuses to start outside a vault.** The
fix built for the launch bar is not reachable by the person the launch bar exists for.
Handing the warm prospect the one-liner before publishing hands them the bug this pass
removed.

Second, still unchanged for six briefings: **record the three compute-lane verdicts**
(~3 min), paste-ready in `.ost-agent/drafts/compute-docket-2026-07-24.md`. Recording
any one of them is what makes v0.9.0's side-by-side visible on real data.

## 2. The next build

**Nothing, until §1 and §3 happen — and unlike the last two briefings, this is not
the agent finding a reason not to build.**

The product is one publish and one message away from its first external operator. Any
feature built before that is built on 208 nodes of founder-and-agent sourcing, for a
user who has still never been contacted, in a week when the strategy that governs
what is worth building changed twice without warning.

**If something must be built**, the honest candidate is the *discoverability* half of
[[A first-run branch that walks a stranger to a vault in one question]] — a `/ost-setup`
front door. v0.11.0 made the first-run state reportable; it did nothing to make it
discoverable, and a stranger who installs a plugin and opens a session still sees no
prompt and no reason to believe anything is waiting. That gap is named precisely in
[[Does a first-run branch actually get a stranger to a working vault]] and is the
single most likely way the warm trial fails quietly.

**Do not build** [[Ship a starter vault whose outcome is a placeholder the human must
replace]] before running its assumption test. It is the cheapest thing here to build
and the most expensive to be wrong about: it is the only candidate that makes the
launch sentence literally true, and it buys that by letting a machine write the
mandate — which is the one rule the rest of this system is built on.

## 3. The highest-information action, and it changed shape this pass

**Hand the one-liner to the warm n=1 participant. Say nothing else for thirty
minutes.**

This replaces "run the cold offer", which the founder declined. It is smaller,
warmer, and available now. The test is written:
[[Does a first-run branch actually get a stranger to a working vault]], with a bar
that is deliberately hard — a committed root Outcome in their own words within 30
minutes, **zero questions asked**, where any clarifying question counts as a
refutation rather than a narrow pass.

**n=1, and this vault must not launder it.** One warm participant cannot clear
[[Cold-offer test - will outside teams hand over real discovery work]]'s 5-of-20
threshold and must not be recorded against it. What it can produce is the **first
external-operator evidence of any kind** in 212 nodes, at the `observed` rung.

**Does v0.11.0 clear the launch bar?** Not literally. *"Setup runs itself"* cannot be
made literally true without the agent inventing an outcome. What is true today is
*"install the plugin, and the session walks you through — it needs one sentence from
you."* Whether that is close enough to send is the founder's call, and it is a
smaller call than it was this morning. It is also **untestable from inside this
building**, which is the point.

## 4. The bias in this briefing, declared

Six passes, six builds the agent could finish alone. This one is the first aimed at a
named external person — and it still could not reach them, because the last step is a
publish credential and a message, neither of which compute may hold.

Read that sentence twice. It is the same sentence the sibling vault's briefing arrived
at from the other direction: the tetrix pass built the arm split its best test needed,
then discovered the test needs ≥100 real strangers nobody has. **Both products spent
this cycle building the apparatus for a conversation neither has had.** That is either
two well-prepared launches or a loop that has found a very sophisticated way to stay
indoors, and one publish would settle which.

Also worth noticing, against the case for restraint the last briefing made: the
v0.10.0 threshold classifier — built here, argued against here — is what made the
*sibling* vault's briefing demand real bars from its own new nodes this pass. Tooling
built for dogfooding changed a decision in another tree twice now. That is a real
argument that this vault is worth maintaining, and no argument at all that anyone else
has this problem.

The standing 2026-07-24 prioritisation is now partly superseded: the target row —
external demand evidence — survives, but the critical path inside it is no longer
cold-offer → recruiting → pre-order. It is **publish → warm n=1 → whatever they say.**

## History

### 2026-07-25 (sixth pass) — this one

Shipped v0.11.0: the MCP server starts outside a vault and reports first run as
`bootstrap: true` state rather than an error; the credential wall names the variable
and the no-key plugin path instead of the SDK's own words; the skill gained a
generated first-run branch that refuses to invent the outcome. Mapped it onto
[[I can't tell another PM 'just run npm install' and have it work]] as *one seam
closed, one halved*. **Mapped v0.10.0, which the previous pass shipped and never
recorded** — the tree spent a cycle recommending against a feature already on `main`.
Found that the threshold extractor misreads a line-wrapped pre-commitment as `absent`.
Added two competing solutions and two assumption tests under the launch-bar
opportunity, including one written against the agent's own design instincts. Rewrote
this file around the founder's mid-week strategy change: free distribution, cold offer
declined, one warm participant gated on the launch bar. npm publish now two releases
behind — and now blocking, because the plugin resolves to the version this pass fixed.

**Outcome of the fifth pass's briefing: §2 ("build nothing") overtaken by events** —
a founder decision and a fresh-user audit named a different build, and it shipped.
§1.1 (publish) not acted on, for a sixth pass. §1.2 (three verdicts) not acted on.
§4 (cold offer) **declined by the founder**, not deferred.

### Superseded — 2026-07-25 (fifth pass)

#### What the fifth pass recorded about itself

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
