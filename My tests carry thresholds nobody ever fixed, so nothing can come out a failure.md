---
type: Opportunity
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-25-pass5'
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Flag a threshold that is still an instruction to choose one]]
[[Refuse to record a result against a threshold that was never fixed]]
[[Make the threshold a field the node carries, not a sentence in its prose]]

**The need (operator's voice):** *"Every one of my assumption tests has a
pre-commitment section, so the tree looks rigorous. Then I go to run one and the
pre-commitment says 'fix the minimum number before starting'. Nobody fixed it. So
whatever comes out, I can read as a pass — and I will, because I want to build the
thing."*

**How this surfaced, with numbers.** v0.9.0's threshold extractor was run over both
live vaults before it shipped. It is a mechanical reading of what is actually in the
node bodies:

| | assumption tests | threshold extractable | contains a number or a bound |
|---|---|---|---|
| ost-agent-meta | 77 | 65 | 57 |
| tetrix-ost | 27 | 27 | **4** |

`tetrix-ost` is the sharp case: **21 of 27** of its extractable pre-commitments open
with *Fix…*, *Decide…*, *Choose…* — they are instructions to pre-commit, standing in
where a pre-commitment should be. This vault is in much better shape (57 of 65 carry
a number or a bound), which is itself informative: the same agent wrote both, and the
difference is that this tree's tests were mostly drafted alongside a specific
disconfirmer while the sibling's were drafted in bulk during ideation.

**Why it matters more than it looks.** The believability ladder, the evidence-debt
gate, and v0.8.0's coverage field are all machinery for making a claim refutable. All
of it sits on top of a threshold that a human wrote before looking. If that threshold
is "decide a threshold", the whole stack is enforcing paperwork around a bar that
does not exist — and the failure is invisible, because every mechanical check passes.
`debt` counts the pair; `gate` clears on any recorded result; nothing has ever asked
whether the thing pre-committed to was a commitment.

**Litmus test (more than one way to address it):** flag the unfixed ones, refuse a
result against one, move the threshold out of prose into a field the tool can require
at creation, or leave it entirely to review. Passes.

**Caveat for a human, and it is a real one.** The distinction between "a threshold"
and "an instruction to set one" is fuzzy, and the cheap mechanical version of this
(does the sentence start with an imperative verb) will be wrong at the edges. A rule
that nags about well-written thresholds gets turned off, and then the genuinely empty
ones come back with it. Whatever gets built here should be a *report* before it is
ever a *refusal* — which is the order "Flag a threshold that is still an instruction to choose one"
and "Refuse to record a result against a threshold that was never fixed" are
deliberately proposed in.

**Provenance:** agent-origin — a fact about two vaults inside this building,
mechanically checked, not a sentence from any user. It sits at the `assertion` floor
for the same reason everything else does, and it is another instance of the hole
"A Context node type for evidence that is true, useful, and not a customer need"
describes: verified fact about our own system, weighted like founder theory.

## History
- 2026-08-05 unlinked "Do named unfixed thresholds actually get fixed" — not a parent-child relation the OST hierarchy supports — every tree walk counted it as structure, so a cross-reference read as a child

## Why this matters more than the node already claims — and the tool gap that blocks repairing it (2026-08-21 unattended sweep)

This node argues the case on rigour: an unfixed bar means every outcome reads as a pass. Reading `src/eval/buildable.ts` this pass turns that into something sharper and more mechanical — **threshold-boundness is what decides whether a solution reaches a builder at all.**

`confirmPermit` treats a `no-spec` run (the instrument names a spec nobody has written) conditionally:

```
if (observed.observation === "no-spec") {
  if (permit.thresholdBound) return permit;   // permit stands
  return { cleared: false, … }                // nothing to build to
}
```

A weak red keeps its build permit **if and only if** the test carries a bound threshold. The code justifies this from a real lifecycle in this vault — "Declare a required tool set and check a pass refuses before doing any work", red 2026-08-06 with "No test files found", green 2026-08-07, where the builder found the path empty and built to the pre-committed bar instead.

So an unfixed threshold is not only an epistemic problem. It is the difference between a test that hands a builder a definition of done and one that hands them nothing — and given that an agent cannot author spec files (see "A pass that cannot see the repository cannot set an instrument at all"), the threshold is frequently the *only* thing carrying that definition. The rollup's per-bucket counts of tests stating no fixed bar are therefore a direct count of permits that cannot survive contact with `confirmPermit`.

**The tool gap.** No tool on any agent surface sets a threshold on a test that already exists. `ost_create_node` accepts a `threshold` argument at creation; after that there is nothing — `ost_set_instrument`, `ost_set_status` and `ost_set_evidence` each own their field, `ost_edit_node` takes prose only and explicitly leaves frontmatter untouched, and no `ost_set_threshold` exists. This is a genuine asymmetry with the instrument field: `ost_set_instrument` exists precisely so passes can retrofit tests written before instruments existed, and its tool description makes that argument at length ("Use this to work through tests written before instruments existed"). The identical argument applies to thresholds, and the identical tool is absent.

The consequence is that every existing test with an unfixed bar is unrepairable from an agent surface, however clearly a pass can see what the bar should be. This sweep hit it directly: it could give three new tests bound thresholds at creation and could not fix a single existing one.

**For a human:** this looks like a missing sibling to `ost_set_instrument` rather than a design decision — but it may be deliberate (a threshold is a pre-commitment, and letting an agent revise one after the fact is exactly how a bar gets moved to meet a result). If it is deliberate, that reasoning deserves recording, because the asymmetry currently reads as an oversight. If it is not, the repair is small and unblocks the lever this node is about.

_First-party read of this product's own source via `ost_read_repo`, plus the tool surface this sweep actually held. Grounds feasibility only; rung unchanged at the floor._

## Three readers of "fixed bar" disagree, and the operator reads the loosest one (2026-08-22 unattended sweep, repo sight held)

`thresholdKindOf` sorts every test into four kinds — `bound`, `instruction`, `prose`, `absent`. **Three separate consumers read that classifier and draw the line in two different places**, which means this vault's headline number and its debt report are counting different sets, and nothing says so at either surface.

| Consumer | Treats as a defect | Treats as fine |
|---|---|---|
| `computeUnfixedThresholds` (what `ost-agent debt` lists as `unfixed`) | `instruction`, `absent` | **`prose`**, `bound` |
| `renderRollup` ("N of M test(s) state no fixed bar") | `instruction`, `absent`, **`prose`** | `bound` |
| `confirmPermit` (`permit.thresholdBound`) | `instruction`, `absent`, **`prose`** | `bound` |

`prose` is the whole disagreement, and both sides argue their case in comments. `coverage.ts` excludes it deliberately: "`prose` — neither. Often a perfectly good falsifiable bar written in words ('the piece survives a page reload'), which is why it is not flagged." `rollup.ts` includes it just as deliberately: "`bound` is the only kind that names a number fixed in advance; `prose`, `instruction` and `absent` all leave the bar to be decided after the run, which is the same as having none."

**Why this matters to a reader rather than only to a maintainer.** The rollup line is the one an operator actually sees — it is pasted at the head of every unattended firing's prompt and read in notifications. So the number in front of the operator uses the strict definition, while the tool they would run to *find out which tests* (`ost-agent debt`) uses the loose one and will not name the `prose` ones at all. A person who reads "14 of 50 test(s) state no fixed bar" and then goes looking for fourteen tests will be handed a shorter list, with no explanation of the gap. That is the failure mode this opportunity is about, one level up: a count that cannot be reconciled with the thing it counts teaches its reader to stop trusting it.

**Which line is right is a real question and not this pass's to settle.** `confirmPermit` siding with the rollup is the strongest argument for the strict reading — a `no-spec` instrument on a `prose` test loses its permit, so in the one place the distinction spends money, `prose` already counts as unfixed. The argument for the loose reading is equally real: a bar in words is a bar, and nagging about well-written thresholds is how a report gets ignored, which `coverage.ts` says outright.

**The cheap repair, if anyone wants it, is neither of those.** Make the rollup line name its own definition — "N of M state no bar fixed in advance (`bound`); `ost-agent debt` lists the subset that states none at all" — so the two numbers stop looking like the same measurement. That is a wording change, not a classifier change, and it does not require deciding the question above.

**Not acted on.** Nothing here changes a classifier, a threshold or a lane; it names a disagreement between three readers of one function. A human choosing the strict reading should expect `ost-agent debt`'s unfixed count to jump.

_Method: first-party `ost_read_repo` of `src/eval/coverage.ts`, `src/eval/rollup.ts` and `src/eval/buildable.ts` in full. Nothing executed — the three call sites are read off the source, not observed. Grounds feasibility only; silent on whether anyone wants either number changed. Rung stays at the `assertion` floor._

## Correction: the bound-threshold escape is unreachable for any instrument written today (2026-08-23 unattended sweep, repo sight held)

The 2026-08-21 section above says a weak red "keeps its build permit **if and only if** the test carries a bound threshold", and draws from it the conclusion that "the threshold is frequently the *only* thing carrying that definition" of done. The code it quotes is real and quoted accurately. **The conclusion does not follow, because that branch cannot be reached by an instrument an agent writes now**, and a pass planning work on the strength of it would write bound thresholds expecting them to unblock a builder. They do not.

Read first-party this pass from `src/eval/buildable.ts` and `src/ost/instrument.ts`, in full:

1. `permitFrom` only ever clears on `live = withInstruments.filter(t => observedRed(t.test) && !observedGreen(t.test))`. A permit that never clears is never minted.
2. `observedRed` matches `/\*\*red\*\*/i` against the node's own Instrument Log lines. A `no-spec` run writes `- <date> **no-spec** (exit …)`. That string contains no `**red**`, so `observedRed` is false.
3. `confirmPermit` — the function holding the `thresholdBound` escape — opens with `if (!permit.cleared || !permit.instrument) return permit;`.

So the sequence is closed: a new instrument naming an absent spec files `**no-spec**` → `observedRed` is false → `permitFrom` never clears → `confirmPermit` returns at its first line and the `thresholdBound` branch is never evaluated. **The escape exists only for permits already cleared on a recorded `**red**` line** — that is, reds filed before the `no-spec` marker existed, which `confirmPermit` re-checks at spend time. Its own comment says as much ("Reds recorded before the distinction existed are re-checked at spend time"); the section above generalised a backward-compatibility path into a live route.

**What a `no-spec` test actually is: waiting, not dead.** Because neither `observedRed` nor `observedGreen` matches its log, such a test stays in `testsAwaitingVerification` permanently and is re-run every pass. `runInstrument`'s own comment says this is deliberate — the missing-file case short-circuits before the runner starts precisely so "a queue full of un-written specs costs nothing to re-check every pass … that queue is meant to be re-checked until somebody writes them." The moment a builder writes the spec, the next verify files a genuine red and the permit becomes available. Nothing is lost; nothing is unblocked in the meantime.

**Two consequences worth separating, because they point opposite ways.**

- *For this node's own claim:* a bound threshold is still worth writing, and the reason the node gives on rigour is untouched — an unfixed bar still means any outcome reads as a pass. What is wrong is only the added mechanical claim that a bound threshold carries a definition of done past `confirmPermit` for new work.
- *For whoever plans the instrument bucket:* this closes the one apparent loophole in the argument recorded on "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed" that no agent surface can author a strong red. A reader comparing the two nodes would reasonably have concluded that a bound threshold was the third case that node says does not exist. It is not. That node's conclusion survives; only its step-2 reasoning (which argues from `observedRed` alone) is less complete than the path traced here.

**Still true and unchanged by this correction:** no tool on any agent surface sets a threshold on an existing test, so the asymmetry with `ost_set_instrument` named above stands, and the ask to a human about whether it is deliberate stands with it.

_Method: first-party `ost_read_repo` of `src/eval/buildable.ts`, `src/ost/instrument.ts` and `src/knowledge/instruments.ts` in full. Nothing executed — the control flow is read off the source, not observed at runtime, and that is the honest limit on this correction. Grounds feasibility only; no result recorded and the rung is unchanged at the floor._

## Issues
- 2026-08-30 2026-08-30 unattended sweep — a mechanism finding that bears directly on this node's subject, observed first-party by hitting it. This tree records that 260 of its 266 reds read "No test files found", and the standing reading is that agents reserve filenames instead of writing specs. There is a second cause, and it is structural rather than behavioural: **the instrument grammar cannot express a strong instrument against an existing spec file.** This pass tried, in the exact form the unattended firing prompt itself gives as its worked example of a strong instrument, and was refused twice by `ost_create_node`: `npx vitest run test/evidence/age-out-preserves-novel.test.ts -t "twenty old records ... stays listed"` was rejected as containing shell punctuation, and the unquoted single-token variant `-t uncited-signature-collapse` was rejected with "is not an instrument form. The allowed forms are: vitest-spec (`npx vitest run <path>.test.ts`)". So the only accepted shape is a bare spec-file path. Against a green suite that leaves exactly one way to be red — name a file that does not exist — which is the weak red by construction. An agent following the prompt's own instruction to prefer a spec whose assertions go red over one whose only red is a missing file cannot comply while the grammar stands. Worth a human's decision, and there are at least two routes: allow a `-t` filter as a separate typed argument rather than as free text inside the command string, or accept that instruments name new files and move the strength requirement onto the written assertions instead (this pass wrote those assertions out in full in the test body, which is the best available substitute). Recorded here rather than as a new node because it is evidence about a cause this node already names, not a new need. Not instrumented; no test was run and no result is recorded.

## 2026-08-31 — the instrument-grammar refusal confirmed from source, and the decision it puts to a human is narrower than it looked

Kept short. The 2026-08-30 Issues note above establishes, from two refusals it received, that the instrument grammar accepts only a bare spec path and rejects a `-t` filter. This pass read `src/knowledge/instruments.ts` in full rather than inferring from refusal messages. **The note is accurate.** `INSTRUMENT_FORMS` holds exactly one entry, and its pattern is anchored at both ends — `/^npx vitest run (?<target>[A-Za-z0-9][A-Za-z0-9._/-]*\.test\.ts)$/` — so nothing may follow `.test.ts`. A separate `SHELL_METACHARACTERS` guard refuses quotes independently. Both refusals that note received were correct and neither was a near-miss.

**What the source adds that a refusal message could not: the restriction is argued, not incidental.** The module's docstring states the reason — the agent authors the instrument, so "an agent that could write any shell string could write one that exits 0 and hand itself a passing test — the tree's credibility spent on `true`." The bar for admitting a new form is stated in the same place: "the form's verdict is produced by committed code, reviewed under the repo's own gates, and reproducible by anyone who runs it." And adding one is explicitly called "a real decision: it widens what an unattended pass can put its name to."

**Why that narrows the human's question.** The 2026-08-30 note offers two routes and treats them as comparable. They are not, once the stated bar is applied. A `-t` filter passed as a *separate typed argument* — never concatenated into the command string, so no metacharacter guard is involved — leaves the verdict exactly where the docstring requires it: produced by committed code in a reviewed spec file. It narrows *which* assertions run; it cannot author an outcome, because an agent that names a test title that does not exist gets a non-zero exit rather than a green. So route one appears to satisfy the module's own admission bar rather than to trade against it, which is a different claim from "widen the grammar and accept more risk". A human deciding this should weigh whether that reading holds, because if it does, the single largest structural cause of weak reds in this vault is removable without loosening the anti-fabrication property the closed vocabulary exists to protect.

**What this does not establish.** Whether vitest's `-t` on a non-matching title exits non-zero or exits 0 having run nothing was **not** verified — nothing was executed this pass, and that detail decides the whole argument above. If it exits 0 on no matches, a `-t` filter is a way to author a green and route one is dead. That is the one thing to check before acting on this, and it is a spec's worth of work rather than a discussion. Nothing here changes a classifier, a threshold, an instrument or a lane, and this node's rung is unchanged.

_Method: first-party `ost_read_repo` of `src/knowledge/instruments.ts` in full (`"truncated": false`). Read off the source; nothing executed. Grounds feasibility only._
