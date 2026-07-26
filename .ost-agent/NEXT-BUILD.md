# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-26 (autonomous bootstrap loop, seventh pass)._

---

## What changed since the last briefing

**Shipped: v0.12.0 — `/ost-setup`** (`d3efbbd` on `main`), which is the build the last
briefing named as the honest candidate if anything was to be built.

The gap it closes is one sentence long and the last two releases both walked past it.
v0.11.0 made first run **reportable** — an empty directory answers `bootstrap: true`
instead of failing to connect, and the skill grew a branch for it. Both are only reachable
by someone who *already asks for discovery work*, which is exactly the thing a stranger
installs this product to learn how to do. The slash-command menu is where a person who has
just run `/plugin install` looks. So the branch now has a name in it.

- `/ost-setup` calls `ost_next_work`; on `no-vault` it asks the one question it may not
  answer — *what outcome do you want this tree to serve?* — reads the answer back verbatim,
  and runs `ost-agent init <folder> --outcome "<their words>"`. On `no-outcome`, the same
  through `set-outcome`. On an existing vault it reports and **stops**: no re-initialising
  over a live tree, no touching an Outcome someone already chose.
- **Generated, not written.** `scripts/gen-skill.ts` renders it from `OST_RULESET.firstRun`
  — the same source `SKILL.md` renders from — and the drift test fails on either being
  stale. Two hand-maintained copies of the branch that must never invent the outcome would
  drift, and the drift would be silent.
- **Four named shell grants, not a shell.** `Bash(ost-agent init:*)`,
  `Bash(ost-agent set-outcome:*)` and their `npx` forms, with a test asserting the shape of
  every grant. A bare `Bash` would hand a shell to the product whose whole promise is that
  it holds no tool capable of a destructive action.
- A new ruleset rule states the principle so both brains learn it: *reporting first run is
  not the same as being findable.* Both bootstrap messages now name the command, so a
  person arriving through the tool layer and one arriving through the menu land in the same
  place.
- 351 tests across 53 files (up from 340 / 52), `tsc` clean.

**Two hygiene findings, both about counts this product publishes.**

*The threshold classifier's line-wrap misread was reproduced live, by accident, by this
pass.* A new tetrix test carrying a sample floor, a numeric bar and an explicit revert
condition was classified `absent`, because its bold pre-commitment lead-in wrapped across a
line. Moving the lead-in onto one line — not one word of the threshold changed — moved it
to bound. **Every `absent` count this feature has ever published is a floor, not a
measurement.** Second confirmed sighting; still flagged rather than fixed, because changing
the extractor changes a published number.

*The line-wrapped wiki-link defect recurred three times, in this pass's own writing, in a
pass whose brief included flagging it — the third of them inside the paragraph of this very
file that declares it a defect.* Six occurrences across both vaults in three days, all from
prose wrapping, none caught by anything, every one of them repaired only because a
throwaway scan was run by hand before committing. Discipline has now been tried and has
failed six times, by the party that keeps writing the flag. It is filed as a product
defect: [[Refuse a wiki-link that contains a newline]], under
[[I opened the vault in Obsidian and the agent lost half the tree]], with a test that
pre-commits to killing the rule on a single false positive or on proving redundant with
the existing dangling-link check.

## 1. The one thing only you can do, and it is now the binding constraint on everything

**`npm publish` 0.10.0, 0.11.0 and 0.12.0** (~2 min). `npm whoami` → `ENEEDAUTH`; this
environment holds no publish credential and must not. `npm pack --dry-run` packs 138 files
cleanly, so the package is fine.

**Why this has stopped being a chore and become the whole critical path.** The plugin's MCP
server runs `npx -y ost-agent@latest mcp`, which today resolves to **0.9.0 — the version
that refuses to start outside a vault.** So a stranger who installs this plugin right now
gets the exact failure v0.11.0 was built to remove, and never reaches the front door
v0.12.0 was built to add. **Two consecutive passes have built for a launch bar that a
two-minute command stands in front of.** Since the free-distribution decision, distribution
is the critical path for every external-evidence hope in this tree, and the distance
between this repo and its first outside operator is now exactly one command and one message.

Second, unchanged for seven briefings: **record the three compute-lane verdicts** (~3 min),
paste-ready in `.ost-agent/drafts/compute-docket-2026-07-24.md`. Recording any one of them
is what makes v0.9.0's side-by-side visible on real data. This vault has never recorded a
verdict.

## 2. The next build

**Nothing. And this time it is not a judgement call — it is the third pass in a row saying
it, and the reason has narrowed to a single fact.**

The product now has a working first-run path, a discoverable front door, and no user who
can reach either, because the published version is three releases behind. Building a fourth
thing for a stranger who cannot install the first three is not restraint, it is denial.

**If something must be built**, the cheapest honest candidate is
[[Refuse a wiki-link that contains a newline]] — a regex in the existing invariant pass and
one test, serving a defect observed four times in the working artifacts of both live
vaults. It is smaller than the annotation that reported it. It is also, unmistakably,
another piece of tooling this loop built for itself, and it should be read that way.

**Do not build** [[Ship a starter vault whose outcome is a placeholder the human must replace]] before running its assumption test. It is the cheapest thing here to build and
the most expensive to be wrong about: it is the only candidate that makes the launch
sentence literally true, and it buys that by letting a machine write the mandate — the one
rule the rest of this system is built on.

## 3. The highest-information action

**Publish, then hand the one-liner to the warm n=1 participant. Say nothing for thirty
minutes.**

The test is written: [[Does a first-run branch actually get a stranger to a working vault]],
with a bar that is deliberately hard — a committed root Outcome in their own words within
30 minutes, **zero questions asked**, where any clarifying question counts as a refutation
rather than a narrow pass. Its threshold was **not** touched this pass, though the pass
shipped the feature it tests; the annotation added to it says so explicitly.

**n=1, and this vault must not launder it.** One warm participant cannot clear
[[Cold-offer test - will outside teams hand over real discovery work]]'s 5-of-20 threshold
and must not be recorded against it. What it can produce is the **first external-operator
evidence of any kind** in 214 nodes, at the `observed` rung.

**Does v0.12.0 clear the launch bar?** Closer than v0.11.0, and still not literally.
*"Setup runs itself"* cannot be made literally true without the agent inventing an outcome,
which is the one thing it may never do. What is true today is *"install the plugin, type
`/ost-setup`, and it walks you through — it needs one sentence from you."* Whether that is
close enough to send is the founder's call. It is also **untestable from inside this
building**, which is the point.

## 4. The bias in this briefing, declared

Seven passes, seven builds the agent could finish alone. Two of them aimed squarely at a
named external person, and neither reached them, because the last step is a publish
credential and a message.

Read that against the sibling vault's briefing, which arrived at the same place from the
opposite direction: the tetrix pass removed the last mechanical obstacle to that product
being *found*, and in the same run confirmed there is nobody yet to find it. **Both products
have now finished their apparatus.** Neither has met a customer. That is either two
well-prepared launches or a loop that has found a very sophisticated way to stay indoors —
and one publish and two messages would settle which, this week.

One thing worth noticing on the other side of the ledger, because it is the strongest
standing argument for maintaining this vault at all: tooling built here for dogfooding keeps
changing decisions in the sibling tree. v0.10.0's threshold classifier made the tetrix
briefing demand real bars from its own new nodes, twice — and this pass it caught, and then
was caught by, its own line-wrap defect while doing it. That is a real argument that the
product works on the one operator it has, and no argument at all that anyone else has this
problem.

## History

### 2026-07-26 (seventh pass) — this one

Shipped v0.12.0: `/ost-setup`, the first-run front door. Generated from
`OST_RULESET.firstRun` alongside `SKILL.md` with the drift guard extended to it; four
named shell grants asserted by test; both bootstrap messages now name the command; a new
ruleset rule states that reporting first run is not the same as being findable. Mapped it
onto [[A first-run branch that walks a stranger to a vault in one question]] and annotated
its assumption test **without touching that test's threshold**, though this pass shipped
the feature under test. Reproduced the v0.10.0 threshold classifier's line-wrap misread
live and by accident, and recorded that every `absent` count this feature publishes is a
floor rather than a measurement. Caused two more line-wrapped wiki-links in the sibling
vault — fourth and fifth occurrences of a defect this loop has flagged three times — and
filed the mechanical fix as [[Refuse a wiki-link that contains a newline]] with a test that
pre-commits to killing it on one false positive. npm publish now **three** releases behind
and named as the binding constraint on the whole tree rather than as a chore. 214 nodes,
`check` PASS with 0 violations.

**Outcome of the sixth pass's briefing: §2's named candidate shipped** — the
discoverability half of the first-run branch. §1.1 (publish) not acted on, for a seventh
pass, and it is now blocking. §1.2 (three verdicts) not acted on. §3 not acted on: the
warm participant has still not been contacted, and cannot usefully be until §1.1 happens.

### Superseded — 2026-07-25 (sixth pass)

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
