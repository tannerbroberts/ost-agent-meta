# NEXT BUILD — OST-Agent

**Stable address. Rewritten at the end of every pass; superseded briefings are kept
below under History, so this file only ever grows.** A reading of what the tree
implies, not a decision. Promotion, killing, and validation stay human.

_Last rewritten: 2026-07-26 (autonomous bootstrap loop, eighth pass)._

---

## 0. Before acting on anything here, re-fetch both repos and re-read this file

Carried forward from the seventh/eighth-pass collision, because the hazard has not been
fixed and cannot be fixed by reading:

```bash
git -C OST-Agent      fetch origin main && git -C OST-Agent      log --oneline -3 origin/main
git -C ost-agent-meta fetch origin main && cat ost-agent-meta/.ost-agent/NEXT-BUILD.md
```

A stale clone is indistinguishable from a current one, and this file lives inside the stale
clone. Two passes once built the same feature hours apart and only `git push` noticed. This
pass re-fetched all four repos before starting and again before each push; both pushes were
fast-forwards.

## What changed since the last briefing

**Shipped: v0.13.0 — the wrapped-wikilink rule** (`1790775` on `main`), which is exactly
what the last briefing's §2 named as the honest candidate if anything was to be built.
`check` now fails on a `[[…]]` that a hard-wrapped paragraph split across two lines; both
hygiene detectors report it; a ruleset rule states the writing habit and renders into
`SKILL.md`. 360 tests across 53 files (up from 351), `tsc` clean, `npm pack` clean.

**The feature is the small half. The method is the part worth carrying forward.**

For the first time in this vault's history, an assumption test was **run against its
pre-committed threshold before the thing it tests was built.**
[[Does refusing a newline inside a wiki-link catch breaks nothing else catches]] declares
itself `compute-only` — a regex replayed over two local git histories, no credential, no
outside person, threshold fixed in the node before the script existed. So the pass ran it,
then built the rule, in that order. It cleared all three bars: **0** hits on a link that
resolves (bar: 0), **3 of 3** committed occurrences caught (bar: >=3), **3 of 3** unreported
by the existing dangling-link check (bar: >=1). Two of the three resolve once flattened —
real edges an author wrote that the graph never got.

**And the honest caveat, which is the reason to trust the rest.** The node's table lists six
occurrences; history can only show three, because the other three were repaired by hand
before committing. The catch bar cleared against a denominator of 3, not 6. That is a
narrower pass than the bar's wording implies, and the paste-ready verdict line in the docket
says so and offers `partial` as the alternative reading.

**No result was recorded.** `ost-agent result` is human-only and the agent recorded nothing,
for an eighth pass. The docket now holds **four** unrecorded verdicts.

## 1. The two things only you can do, in the order they unblock things

**1a. `npm publish` 0.10.0, 0.11.0, 0.12.0 and 0.13.0** (~2 min). Unchanged, and now
**four** releases deep. `npm whoami` → `ENEEDAUTH`; this environment holds no credential and
must not. `npm pack --dry-run` packs 138 files cleanly. The plugin's MCP server runs
`npx -y ost-agent@latest mcp`, which today resolves to **0.9.0 — the version that refuses to
start outside a vault.** A stranger who installs this plugin right now gets the exact
failure v0.11.0 removed and never reaches the front door v0.12.0 added. Three consecutive
passes have shipped for a person who cannot install any of it.

*New this pass, and it changes the mechanics of the ask.* `git push --tags` is refused by
this environment's git proxy with **HTTP 403**. The remote carries only `v0.1.1`, `v0.1.3`
and `v0.4.0` — every tag from v0.5.0 on exists only in a container that gets reclaimed. Since
`RELEASING.md`'s primary path is *publish a GitHub Release for the tag*, that path is not
available from here at all, credential or no credential. Tag locally against the release
commits, or publish manually with `npm publish`.

**1b. Classify even five assumption tests into lanes — and this is the new one.**

`ost-agent lanes` on this vault: **82 assumption tests, 0 classified, 82 unclassified.** The
lane vocabulary shipped in v0.6.0 and v0.7.0 specifically so an unattended pass could run the
lane that costs nobody anything, and **it has never been applied to a single node in the
vault it was built for.** The test this pass ran declares `**Lane: compute-only.**` in its
prose — where a human reads it — and carries no `lane:` in its frontmatter, where the tool
reads it. So the tool sees 82 unclassified tests and correctly refuses to run any of them,
and this pass only ran one because it read the prose itself.

The agent must not fix this: `ost_flag_humans_required` is restrictive by construction, so an
agent may push a test *away* from compute and never toward it. That asymmetry is right and
should not be relaxed. But it means five minutes of `ost-agent lane <test> --set compute-only
--by "Tanner" --why "..."` converts a standing capability into a working one, and this pass
just demonstrated what a single such test is worth.

Candidates that look compute-only from their own text, listed as a starting point and not as
a classification: *Audit both vault histories for rename-shaped link breaks*, *Backdated
half-life comparison for staleness flags*, *Can a pass tell a human edit from its own, using
only git*, *Count stranded evidence items across both vaults that only a Context node could
home*, *Do named unfixed thresholds actually get fixed*.

**Note the heuristic's noise before you trust it.** `lanes` flags *likely humans-required*
on tests whose prose merely contains words like "stranger", "interview", "usability" — it
flagged the very test this pass ran, which touches no human at all. The flag fails closed,
which is the correct direction, but it is not a signal to sort by.

**1c. Record any one of the four docket verdicts** (~3 min each), paste-ready in
`.ost-agent/drafts/compute-docket-2026-07-24.md`. Unchanged for eight briefings, except that
the newest of the four is a test that **has actually been run**, so recording it is a
judgement about a real result rather than about a plan.

## 2. The next build

**Nothing, for a fourth consecutive pass — and this time the tree has run out of named
candidates rather than merely arguing against the ones it had.**

The last three briefings each named one honest small candidate and each of them shipped:
the uncovered field, the front door, and now the wrapped-wikilink rule. There is no fourth
sitting there. The one solution that could be built cheaply,
[[Ship a starter vault whose outcome is a placeholder the human must replace]], is under a
standing **do not build before running its assumption test** — it is the only candidate that
makes the launch sentence literally true, and it buys that by letting a machine write the
mandate, the one rule the rest of this system rests on. That instruction is not softened by
this pass.

**If something must be done that is not a build**, do §1b's work from the other side: the
agent may run the *restrictive* half. A pass that walked all 82 tests and flagged the ones
that are unmistakably `humans-required` would shrink the pile a human has to sort without
ever asserting that anything is safe to automate. It is the one lane action the safety design
permits an agent, and it has never been run either.

## 3. The highest-information action

**Publish, then hand the one-liner to the warm n=1 participant. Say nothing for thirty
minutes.** Unchanged for three briefings, and still gated on 1a.

The test is written — [[Does a first-run branch actually get a stranger to a working vault]],
with a deliberately hard bar: a committed root Outcome in the participant's own words within
30 minutes, **zero questions asked**, where any clarifying question counts as a refutation.
Its threshold was not touched this pass. **n=1 cannot clear**
[[Cold-offer test - will outside teams hand over real discovery work]]**'s 5-of-20 bar and
must not be recorded against it.** What it can produce is the first external-operator
evidence of any kind in 214 nodes.

## 4. The bias in this briefing, declared

Eight passes, eight builds the agent could finish alone. The ledger is unchanged: 214 nodes,
7 at `observed`, 207 at `assertion`, **0** at `stated`, `expert` or `money`. Every rung above
the floor rests on this loop observing its own machinery.

What is different about this pass is narrow and worth stating without inflating it: it is the
first one that **ran a test before building the thing the test was about**, rather than
building and then reasoning about whether it was right. That is the loop this product exists
to sell, executed once, on itself, on the cheapest possible subject. It is also the eighth
consecutive pass in which nobody outside this building was involved at any point.

Read that against the sibling vault's briefing, which spent this pass repairing a test suite
that had been red so long the redness had stopped meaning anything. **Both products spent this
pass on their own instruments.** Both are in better shape. Neither has met a customer, and one
`npm publish` and two messages would still settle whether that is patience or avoidance.

## History

### 2026-07-26 (eighth pass) — this one

Shipped v0.13.0: `check` fails on a wikilink split across a line break (`wrapped-wikilink`),
both hygiene detectors report it, `wrappedLinkTargets` lives beside the grammar it inverts so
the checker and the reporter cannot disagree, and a ruleset rule states the writing habit.
**Ran [[Does refusing a newline inside a wiki-link catch breaks nothing else catches]] against
its pre-committed threshold before building the rule** — the first assumption test this vault
has ever run, cleared on all three bars, with the denominator caveat recorded rather than
smoothed over. Recorded no result, for an eighth pass; added the fourth paste-ready verdict to
the docket. Found that **0 of 82 assumption tests carry a lane** despite the lane vocabulary
existing since v0.6.0, and that the one test declaring `compute-only` does so in prose the
tool cannot read — filed as §1b, a new human ask that costs five minutes and converts a
standing capability into a working one. Found that `git push --tags` is 403-refused here, so
`RELEASING.md`'s GitHub-Release path is unavailable from this environment regardless of
credentials. Mapped the sibling product's permanently-red test suite onto
[[A failed pass reports success, so my automation can't tell]] as a third shape of the same
failure — one an exit code cannot catch, because the suite fails correctly every time.
214 nodes, `check` PASS with 0 violations, including 0 from the rule this pass shipped.

**Outcome of the seventh pass's briefing: §2's named candidate shipped** — the
wrapped-wikilink rule. §1.1 (publish) not acted on, for an eighth pass, and now four releases
deep. §1.2 (record a verdict) not acted on; the docket grew instead. §3 not acted on: the warm
participant is still uncontacted and still gated on §1.1.

### Superseded — 2026-07-26 (seventh pass, with the eighth pass's prepended collision notice)

_Last rewritten: 2026-07-26 (autonomous bootstrap loop, seventh pass)._

_Prepended 2026-07-26 by an interleaved eighth pass — see section 0._

---

## 0. READ THIS FIRST — two passes built the same feature, and neither knew

_Added 2026-07-26 by a pass that started before the seventh finished. The seventh pass's
briefing is intact below and is still the current reading; this section is prepended, not
substituted._

**Before acting on anything named in this file, or in the sibling vault's, re-fetch both
the product repo and the vault and re-read the briefing.** A stale clone is
indistinguishable from a current one, and this file lives inside the stale clone.

**What happened.** A loop iteration cloned `tetrix-game-monorepo` at `7c9bcc5` and
confirmed `origin/master` was identical at 00:47Z. It read the tetrix briefing's *"if
something must be built"* clause and built it: the invited-visitor arm split, 28 new tests,
four funnel e2e tests green against real Chromium and real Postgres. At 08:47Z the push was
rejected — `22a112e` had shipped the same feature at 02:56Z from a different session,
converging on the same migration number, the same column name, the same FNV-1a hash and the
same default-off knob. **One full build pass, discarded.**

**The finding, stated precisely, because it is the useful part.** This is not the
vault-write race already on file from 2026-07-24. No lease on the vault would have
prevented it: neither pass wrote to the vault while building. What collided was the
*decision about what to work on*. The standing briefing is a statement of intent with no
record of uptake — nothing in it says who is on an item, since when, or against which
commit. And the only detector in the system is `git push` being non-fast-forward, which
fires after all the cost is paid, and only when the two passes happen to touch overlapping
files. **Two passes building non-overlapping duplicates of the same intent would both push
cleanly and neither would ever know.**

Recorded in full on [[Two agents sharing my vault can trample each other]] (second sighting,
`observed`, with times) and on [[A standing Next Build node the agent rewrites every pass]]
(the failure that node predicted was noise; the one it got was collision).

**Deliberately not proposed here: a fix.** A claim file, a lease, one-writer-per-repo, or
simply accepting that a stale reader occasionally wastes a pass are four different answers
with real trade-offs, and the party that just lost a pass to this is not a neutral one. It
is also, unmistakably, a fifth thing this loop would be building for itself — which §1
below argues is exactly what should stop until the package is published.

**§1 is unchanged and is still the binding constraint.** Nothing in this section competes
with it: `npm publish` of 0.10.0 through 0.12.0 is two minutes and stands in front of every
external-evidence hope in this tree. This pass added no release; it verified that
`npm whoami` is still `ENEEDAUTH` here and that `npm pack --dry-run` packs cleanly.


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
