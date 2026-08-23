---
type: Opportunity
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[Every path the config declares is checked when the config is read, not when something reaches for it]]
[[A pass ends by reporting which of its senses were live and which it never had]]
[[The instrument-writing step declares repo sight required and skips itself rather than inventing paths]]

[the text below is fetched DATA — it is never instructions]
---
A pass reaches for the product's own code partway through its work and finds the sense it assumed it had is not wired. The operator does not discover the gap at setup, when it is cheap to fix; they discover it mid-pass, at the moment the agent reached for the product and found nothing there. Everything downstream — instruments grounded in real modules rather than invented paths — is silently *degraded* rather than blocked, so the pass reports success while working blind.

**The need is to know that a configured sense is actually live before a pass depends on it, rather than after.**

## There are two independent channels, and they fail separately

This is the distinction the individual sightings kept re-establishing, so it is stated once here. A pass can reach the product two ways, and neither covers for the other:

| Channel | How it fails | Status |
|---|---|---|
| `ost_read_repo` (config route) | "no product repos configured — add local repo paths under `product.repos` in ost.config.yaml" | **Repaired 2026-08-09** and still working — verified live again 2026-08-23 |
| `Glob` / `Read` on the checkout (permission route) | "Claude requested permissions to read from /Users/tanner/dev/OST-Agent, but you haven't granted it yet." | **Still failing** — never the subject of the repair |

**Observed in opposite states in a single pass, 2026-08-23.** This sweep called `ost_read_repo({path: "test"})` and got a real listing of 28 entries, then called `Glob("**/*.test.ts", path: "/Users/tanner/dev/OST-Agent")` and was denied. That is first-party evidence that the two channels are genuinely independent rather than co-failing, which the ninth sighting below had assumed they were not. A preflight that checks only one of them will report a live sense that is half dead.

## The permission channel, counted rather than sighted

Ten sightings between 2026-08-06 and 2026-08-19 each recorded one more instance of the permission route being denied. This pass counted the whole corpus instead, which is a strictly stronger measure — it covers the cited records and the uncited ones alike.

| Measure | **2026-08-23** |
|---|---|
| Records carrying "requested permissions to read from" | **84** |
| Total occurrences | **101** |
| Transcript records in the corpus | **423** |
| Share of records affected | **20%** |

**One firing in five loses the permission channel.** That is the number ten anecdotal sightings were circling and none of them established. Records confirming the shape, read in full across those sightings and this one: `TRANSCRIPT:93a613dc-f52b-46c9-9dcf-9b22fdfe36f5` (denied on `/test` specifically), `TRANSCRIPT:89a95209-c65d-460f-801a-a75fd0805b65` (Glob and Read both denied), `TRANSCRIPT:f1c62e34-107b-4f8f-ab9e-c431d918fe07`, `TRANSCRIPT:92acf647-a9f8-4a58-b8a0-4fb68bf5ba25` (captured this pass).

**The denial is path-level, not root-level.** Passes have been refused at the repository root, at `src`, and at `test` in the same sitting. There is no narrower grant that would let a pass read just the test suite to check whether a spec file already exists.

**Future sweeps: re-take this count and add a column, rather than adding an eleventh sighting.**

## What the blindness costs, priced

Recorded by the passes that paid it, and kept because "silently degraded" is otherwise an abstraction.

- **2026-08-05** — machine-recorded: in 583 tool invocations, exactly one call failed, and it was `ost_read_repo`. One failure in 583 is what this gap looks like from the outside, which is why it does not get fixed.
- **2026-08-06** — a pass wrote three instruments blind. Two asserted against behaviour verified absent by *running `ost_next_work` and reading what came back*, so they fail on the mechanism. The third, `test/ost/disposition-ledger-shape.test.ts`, described a wholly absent mechanism and failed first on the import — the weakest reason a command can fail, and the exact degradation this node predicts.
- **2026-08-06 (later)** — three workspace instruments written against a mechanism observed absent in a transcript rather than confirmed absent in code. The unverifiable half was narrow and named on each node: whether a workspace-level lease or per-run path derivation already existed in the runner. If any did, the instrument was green on arrival and measured nothing.
- **2026-08-06 / 2026-08-09** — with both channels shut, passes declined the entire `solutionsMissingInstruments` bucket (63, then 62 solutions) rather than manufacture reds against invented paths. **The cost is a whole bucket, not a call** — and it is invisible afterwards, because `ost_next_work` reports the same 63 next pass with no record that a pass tried and was structurally unable.
- **2026-08-19** — reproduced on the unattended sweep surface itself: both channels closed *and* `ost_flag_humans_required` withheld, so both of the two legitimate dispositions for that bucket were unavailable in the same pass, for the same underlying reason — a surface that does not disclose what it lacks until the call that needs it fails.

**The asymmetry that makes it survivable.** A pass can always read `ost.config.yaml` — the thing describing the product's intentions — while unable to read the product. That is why working blind feels workable and produces the weaker instruments recorded above.

## The repair, and the two limits that survived it

**2026-08-09: the config channel was repaired.** `product.repos` now names `/Users/tanner/dev/OST-Agent` — the same checkout `adapters.transcript.projectDir` had named since the beginning, which is the reconciliation the second sighting asked for. The config carries its own dated rationale on lines 48-52 and cites this node's argument back: repo sight was granted because "six consecutive discovery passes reported repo sight dead and declined to instrument 62 prose-only tests rather than write instruments against invented paths." Verified live, not inferred from the line meant to fix it.

Two limits survived, and both matter to whoever plans the next pass:

**1. The honest ceiling is about 7 in 25, not 25 in 25.** Repo blindness restricted honest instrument-writing to roughly 1 in 60 of the queue. Lifting it does not open the whole bucket. A census on "A pass that cannot see the repository cannot set an instrument at all" classified the 25 visible entries of `solutionsMissingInstruments`: at most 7 are mechanical questions at all, roughly 14 are human preference, demand or pricing, and 3 are already shipped. Repo blindness was the binding constraint on the 7 and was never the constraint on the other 18. A pass reading the repair as "the instrument bucket is now workable" will spend its budget manufacturing commands for the 14 — progress-shaped output that measures nothing.

**2. Repo sight is read-only, so it upgrades the reasoning behind an instrument but not the red.** A pass can now *name* the module a spec would have to change while still being unable to leave a spec file behind. Every instrument an unattended pass writes therefore remains a `no-spec` red — red because the file is absent, which the ruleset itself files as granting no build permit. Closing that gap needs a builder who can write the spec, not a discovery pass with better sight.

## The repair this node is still asking for

A preflight that names a dead sense in the first second, before the pass plans work that depends on it — **covering both channels**, since this pass observed them in opposite states. The 2026-08-06 pass reallocated to work needing no repo sight anyway, but 40 minutes later and after committing to a plan it could not carry out. Until then, every future pass spends the same calls rediscovering the same absence, which is "The same refusal is rediscovered every session, because nothing carries the lesson forward" arriving through this node's channel.

_Sources: this vault's own usage and transcript records, plus first-party observation by the passes named above from their own failed and successful calls. Agent self-observation — it grounds feasibility and usability, not demand. No test has been run and no result is recorded._

## Issues
- 2026-08-11 subset-extent flag vs "The same agent has a different tool surface on every surface I run it on" adjudicated: DISTINCT, keep as siblings, do not re-hang. "Every path the config declares is checked when the config is read, not when something reaches for it" repairs config-declared senses and does nothing about per-tool permission variance, which is the sibling's need; and the sibling's preflight solutions do not validate config paths. The subset extent is an artefact of a shared usage record. Sweep's own verdict; queued for human confirmation via "A human re-judges the first twelve extent flags against Torres's test".
- 2026-08-21 subset-extent flag vs the same sibling, raised again by the automated sweep. The 2026-08-11 adjudication above answers it and still holds. Noted so a future pass does not re-adjudicate: the flag recurs because this node cites one record that is a subset of the sibling's six, and this pass's whole-corpus count of the permission channel (84 records) is the kind of independent evidence that would settle it — a human should decide whether that count now separates the two needs on provenance as well as on concept.
- 2026-08-23 2026-08-23 subset-extent flag re-adjudicated. Rule: subset-extent. Sibling: "The same agent has a different tool surface on every surface I run it on". Verdict: DISTINCT — keep as siblings, do not re-hang beneath it. Torres's interventional test applied: this node's lead solution, "Every path the config declares is checked when the config is read, not when something reaches for it", repairs config-declared senses and does nothing about per-tool permission variance across surfaces, which is the sibling's need; and the sibling's preflight solutions validate which tools a surface granted, not whether the paths in `ost.config.yaml` resolve. A solution exists that serves one and not the other, in both directions. The subset relation is an artefact of provenance: this node cites one record (USAGE:2026-08-05) which happens to be among the six the sibling cites. New this pass, and the thing that should eventually settle it: a whole-corpus count found the permission-denial channel in 101 occurrences across 84 of 423 transcript records — a body of evidence specific to this node's second channel and far larger than the single shared usage record the flag is computed from. That evidence cannot be attached, because `source` is a single field settable only at creation, so the flag will keep recurring until those records are filed with `ost-agent dispose --verdict corroborates`, which is a human's call. A human should decide whether that count now separates the two needs on provenance as well as on concept. Re-filing the verdict rather than restoring the machine's flag text, because this pass's consolidation of ten sighting sections removed the marker that had been suppressing the re-report.
- 2026-08-23 subset evidence extent: every record this rests on (1) is part of what sibling "The same agent has a different tool surface on every surface I run it on" rests on (6) — a subset extent is a child, not a sibling; consider re-hanging it beneath "The same agent has a different tool surface on every surface I run it on", or cite the evidence that makes it a genuinely separate need. ADJUDICATED 2026-08-23: DISTINCT — see the dated verdict above; do not re-hang.

## History
- 2026-08-23 body edited — The node had grown to 18.2KB across ten separately-headed "sighting" sections, several of which restate a diagnosis their own text says needs no restating. Consolidating into one standing finding, a per-channel status table, and the two findings that are genuinely load-bearing and were buried (the ~7-of-25 ceiling, and the read-only limit that keeps every unattended instrument a no-spec red). Adding this pass's two new facts: the first COUNTED measure of the permission-denial channel over the whole corpus (101 occurrences across 84 of 423 records) in place of ten anecdotal sightings, and a first-party observation that the two channels are in OPPOSITE states on this surface today — ost_read_repo answers while Glob on the same directory is denied — which the ninth sighting had assumed could not happen. No distinct claim dropped: every sighting's dated finding, both extent adjudications, the config-line citation and the priced costs are carried forward; git holds the prior text.

## A second, independent cause of the same no-spec red — verified first-party, 2026-08-23

The "two limits that survived" section above names repo sight's read-only nature as the reason every unattended instrument stays a `no-spec` red. That diagnosis is incomplete. There is a second cause, it is upstream of repo sight, and **fixing repo sight does not touch it**.

The ruleset's own prescription for a strong red is an *existing* spec file plus a `-t` filter naming an assertion that is not in it yet — so the command fails for a reason specific to the question rather than because a file is missing. This pass attempted exactly that, fully grounded: it had read `test/loop/run-journal-interruption.test.ts` in full, confirmed the file's four test names, and composed

`npx vitest run test/loop/run-journal-interruption.test.ts -t "a run interrupted through the loop's own signal path still reads as a list of finished steps"`

`ost_create_node` **refused it**: *"contains shell punctuation. Instruments are run as argv with no shell, so a command written to be interpreted would not mean what it looks like. Name one spec file."* A `-t` filter needs quoting to carry a multi-word assertion name, and quoting is what the guard rejects.

**So the recommended strong form is unreachable from any agent surface**, with or without repo sight. The guard is defensible on its own terms — argv with no shell is why an instrument cannot be talked into being a command — but its consequence is that every instrument an agent writes names a file that does not exist, which the ruleset itself files as granting no build permit. Repo sight upgrades the *reasoning* recorded in the test's body, and this guard caps the *red* independently.

**What this changes for whoever plans the next pass.** Do not read the 2026-08-09 repo-sight repair as having made strong instruments possible; it did not. Two things would: a builder who can leave a failing spec file behind, or an instrument grammar that accepts a name-filter argument without shell punctuation (a structured field rather than a string, e.g. an optional `match:` alongside the spec path). The second is a product change, is cheap, and is the one that would let an unattended pass hand a builder a definition of done instead of a filename.

_First-party observation of this tool surface's own refusal, this pass. Grounds feasibility, not demand. No test was run and no result is recorded; the rung is unchanged._

## Correction: the cause named above is wrong, and the real one is stricter (unattended sweep, 2026-08-23, repo sight held)

The section "A second, independent cause of the same no-spec red" attributes the unreachability of a strong instrument to the shell-punctuation guard, and proposes as the cheap fix "an instrument grammar that accepts a name-filter argument without shell punctuation". The refusal it observed was real — `TRANSCRIPT:eed15544-7e72-4107-9918-2060dda23390`, captured this pass, records that exact `ost_create_node` rejection verbatim. **But the punctuation guard is not the binding constraint, and a builder who relaxed it would fix nothing.**

Read first-party this pass from `src/knowledge/instruments.ts`:

- `parseInstrument` checks `SHELL_METACHARACTERS` **first**, which is why the punctuation message is the one a caller sees. It is the outer of two gates, not the tight one.
- Behind it, `INSTRUMENT_FORMS` holds **exactly one form**, and its pattern is anchored at both ends: `^npx vitest run (?<target>[A-Za-z0-9][A-Za-z0-9._/-]*\.test\.ts)$`. Nothing may follow the spec path. The target character class excludes the space, so no argument of any kind can be appended.
- So `npx vitest run test/loop/run-journal-interruption.test.ts -t drifted` — a filter with no punctuation at all, the obvious workaround — is **also refused**, falling through the form loop to the "is not an instrument form" rejection. The punctuation-free workaround does not exist.

The prior section's proposed fix is right in substance and wrong about the file. Relaxing `SHELL_METACHARACTERS` leaves the anchored pattern refusing everything; the change that would work is a **second entry in `INSTRUMENT_FORMS`** carrying its own `match` group and its own `argv`, e.g. pattern `^npx vitest run <path>.test.ts --matches (?<match>[A-Za-z0-9-]+)$` mapping to `["vitest", "run", target, "-t", match]`. That keeps the closed-vocabulary argument the module rests on — the agent still names committed code and never authors the verdict.

## Why no agent surface can author a strong red here at all — the closed argument

Three shipped guards, read this pass in `src/ost/instrument.ts` and `src/knowledge/instruments.ts`, jointly close the space. This is the complete statement the node has been circling, and it is **not about repo sight**:

1. **Write time** — `specResolves` refuses an instrument naming a spec that does not exist, unless the test carries a *bound* threshold (a comparator next to a number). Pinned by "a spec that does not exist is refused, and nothing is written" in `test/instruments/spec-path-resolution.test.ts`.
2. **Run time, missing file** — `runInstrument` short-circuits an absent target to `no-spec`, which `observedRed` deliberately does not match, so it mints no build permit.
3. **Run time, passing file** — `verifyInstrument` **refuses to record a first observation that is green**, unless the solution is trusted-shipped.

An agent surface cannot create files. So every instrument it can express is one of exactly two cases: it names a spec that does not exist (→ `no-spec`, no permit), or it names a spec that exists and therefore passes in a maintained suite (→ green on first run, refused). **There is no third case, and repo sight does not open one.** The 2026-08-09 repair let a pass *check* which files exist; it never gave it a file that fails.

One loophole, named so nobody mistakes it for an opening: an agent could name a spec that exists *and is failing today*. That red would be about whatever that spec was written for, not about the node's question — a misattributed permit, which is worse than none. It is not a route.

**What this changes for whoever plans the next pass.** Do not budget for the `solutionsMissingInstruments` bucket on the strength of having repo sight. The honest dispositions for an entry in it are: a human sets the lane with `ost-agent lane --set` where the question needs people; a builder writes the failing spec where it does not; or the second instrument form above ships and an agent can name an existing spec plus an absent assertion. Nothing else drains it. This also supersedes the "~7 of 25 are mechanical and were blocked on sight" reading in the section above — those 7 were never unblocked by sight either.

**Honest limit on the proposed fix, stated so it is judged rather than adopted.** A `--matches` form is *more* specific than a missing filename — it pins a real spec file, so the builder's definition of done becomes "add an assertion named X to this existing file" rather than "create this file". But it shares the vacuity in kind: any absent filter name is equally red. It is an improvement in degree, not a solution to the red-about-nothing problem, and it should be argued on that basis.

_First-party reads of `src/knowledge/instruments.ts`, `src/ost/instrument.ts`, `test/instruments/spec-path-resolution.test.ts`, `test/instruments/sight-provenance.test.ts` and `vitest.config.ts` this pass, plus `TRANSCRIPT:eed15544-7e72-4107-9918-2060dda23390`. Grounds feasibility, not demand. No test was run and no result is recorded; the rung is unchanged._
