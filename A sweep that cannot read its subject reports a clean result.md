---
type: Opportunity
created: '2026-07-27'
evidence: assertion
authorship: machine
---
#Opportunity #evidence/assertion
[[Every count states the denominator it was taken over]]
[[A check with an empty subject is a failure, not a pass]]
[[Seed every sweep with a known-present instance it must find]]
[[The repair I am asked to make requires rewriting prose no tool will show me]]
[[I overwrote a good instrument because nothing showed me one was already there]]
[[Something can ship, pass its tests, and never be wired into anything that runs]]
[[A measured bar is only re-taken when a pass feels like it, so a fix reads as working long after it stopped]]

**The need (operator's voice):** "The sweep told me 5 and 12. The real answer was 6 and 15. It never said it had failed to open four of the files it was counting — it just counted the ones it could open and printed a total that looked finished."

**What was observed, 2026-07-27 (eleventh pass).** A compute-only history sweep run against both vaults skipped every node whose filename contains an em-dash. Git quotes non-ASCII paths in `--name-only`, `git show <sha>:<path>` failed on the quoted form, and the sweep's error branch was `continue`. Four affected files were never read. The output carried no denominator and no error, so the number looked like a measurement of the whole population when it was a measurement of the readable subset.

**Why this is not the same need as "A failed pass reports success, so my automation can't tell".** That one is about a run that ERRORED and exited 0 — there is a failure, and it is hidden. This one is about a run in which nothing failed: every file the sweep opened, it classified correctly, and it reported exactly what it found. The defect is in what it never reached. A supervisor watching exit codes catches the first and cannot catch the second, because there is no error to catch.

**Why it matters more than the specific bug.** The whole product is a machine that reports on a tree nobody is watching. A count with no denominator is indistinguishable from a complete count, and the operator's only signal is the number itself. This tree has now met the shape three times — a test that could not fail, a lane reader that reported a fragment as a declaration, and now a sweep that measured the subset it could open — which suggests it is a habit of the codebase rather than three accidents.

**Litmus (more than one way?):** yes — reporting unreadables alongside findings, failing on a zero subject count, printing a coverage denominator, and asserting the sweep can see a known-present instance are genuinely different answers.

⚠️ Agent-filed from an observed failure in this pass's own instrument.

## History
- 2026-08-01 evidence: observed → assertion — demoted by the fifteenth pass — B3's rung-unearned guard (v0.23.0-line) shipped after this node was authored; its source is not a TRANSCRIPT: recording, so 'observed' was unearned. Demotion only, per rungs.ts's own remedy.

## Issues
- 2026-08-05 2026-08-05 A first-hand instance of this node's own claim, observed this pass rather than reasoned about: the unattended sweep cannot read its subject's health, and the shape of the gap is that it looks like nothing is wrong. Four tools were called and refused at the permission layer, not by the vault: `ost_check`, `ost_status`, `ost_flag_humans_required` and `ost_read_repo`. The three writes I needed — `ost_create_node`, `ost_append_to_node`, `ost_annotate` — all resolved, so the pass could author freely and could not inspect. That is the asymmetry this node is about, pointing the wrong way. What it cost concretely. The sweep's own instructions say every reported hygiene issue is also an `ost_check` violation, and to repair what can be repaired so the tree is not left red for whoever reads the other gate. `ost_next_work` returned `hygieneIssues: []` this pass, and I have no way to confirm that against the check that actually computes them — a clean hygiene list from one reader is exactly what a sweep that cannot read its subject would report. Same for the believability rollup: I can state that the tree rests on `assertion` because the rollup handed to me says so, not because I read it. Two further consequences worth separating. First, `ost_read_repo` being refused means every instrument written this pass names a spec path derived from the vault's own conventions rather than from the product's actual source tree — the paths follow the established `test/<area>/<name>.test.ts` shape and the areas are real, but no file was read to confirm the module a spec would have to change. The sweep's instructions are explicit that a command whose only red is a missing file is the weakest kind, and preferring a spec that goes red against today's code requires sight this surface does not have. Where a node's own body recorded an observed defect I could write against the mechanism (the wrapped pre-commitment lead-in, the single quoting detector); where it did not, the red is a missing file and each test says so in its own prose rather than pretending otherwise. Second, this is not an argument that the grants are wrong. Withholding the repo is a stated cost decision, and withholding `check`/`status` may simply be a grant nobody added. The finding is narrower and is this node's point exactly: nothing in the pass's output distinguishes "checked and clean" from "could not check", and a human reading this pass's commits has no way to tell which one they are looking at unless a pass says so out loud. ACTION FOR A HUMAN: decide whether an unattended sweep should hold the four read-only analyses (`ost_check`, `ost_status`, `ost_debt`, `ost_gate`) — they write nothing and cannot move a gate — and if the answer is no, consider whether a pass should be required to declare the surface it ran without, which is "Every run records the tool surface it actually had".
- 2026-08-05 **Confirmed live, from inside a sweep — 2026-08-05.** This opportunity is not hypothetical in this vault. During the unattended maintenance pass on 2026-08-05, `ost_read_repo` returned: *"no product repos configured — add local repo paths under `product.repos` in ost.config.yaml so the agent can read what the product is."* The sweep was reading a 920-node tree **about a codebase it could not open a single file of.**

Why this is the node it belongs on rather than a passing inconvenience: the same pass was asked to clear `solutionsMissingInstruments`, 64 solutions whose tests are prose only. An instrument is required to be red today and green when the solution is built. Without repo sight the only red available is *"this file does not exist"* — which is red for the weakest possible reason, cannot distinguish a missing mechanism from a missing filename, and hands a builder no definition of done beyond "create a file here." The pass could still have emitted 64 such commands and reported the bucket cleared. It would have looked exactly like a sweep that had done the work.

That is this opportunity's claim, demonstrated on itself: the blindness does not announce itself in the output. Nothing downstream of a written instrument records whether the agent could see the code when it wrote it, so a tree full of invented paths and a tree full of grounded ones read identically.

**For a human:** setting `product.repos` in `ost.config.yaml` to the OST-Agent checkout would unblock instrument-writing across all 64. Until then, treat any instrument in this vault dated 2026-08-05 or earlier as naming a path rather than a mechanism, and re-derive it once the repo is readable.

## A live instance in the sweep's own summary line — observed first-party, 2026-08-27

This node's two Issues entries argue the shape from tool denials. Here is the shape occurring in the product's own output, in a single sentence, with nothing denied and nothing failing.

`ost_next_work` returned, in its `summary`:

> Of the evidence listed above, 0 record(s) are STALE (captured more than **undefined** day(s) ago — this is a mirror of the source system, not a live read) and 393 carry no capture stamp at all, so their age is unknown.

Two separate defects share that clause, and the second is the one this node is about.

**The literal `undefined` is the cosmetic half.** `evidence.staleAfterDays` is unset in this vault's config, and the summary interpolates the absent value straight into the sentence rather than branching on it. The per-record `mirror.note` on the same response handles the same absence correctly — "no `evidence.staleAfterDays` is set, so nothing here calls that too old" — so the honest branch already exists one field over and the summary does not take it.

**The reassuring `0` is the real half.** With no threshold configured, *no record can ever be stale*, so that zero is not a measurement of the corpus — it is a constant, guaranteed to read `0` across 426 records whatever their ages are and whatever the adapters did. It is this node's claim exactly: a count over an empty predicate, printed next to 426 real records, in a sentence whose grammar asserts a comparison was made. An operator reading "0 records are STALE" concludes the mirror is current. Nothing was checked. Compare the adjacent clause in the same sentence, which does it right: "393 carry no capture stamp at all, so their age is unknown" states the gap instead of scoring it as a pass.

**Where it lives.** The summary is composed in `src/mcp/next-work.ts` (the module's own doc-comment names it "the only place that answer is computed"). The correct behaviour is the one the file already applies to `Truncation`, `ScopeAccounting` and `Withheld`, each of which carries a doc-comment saying a number reported without what it was taken over "would read as the whole truth" — the staleness clause is the one count in this response that does not follow that rule.

**Which of this node's children it argues for.** "Every count states the denominator it was taken over" and "A check with an empty subject is a failure, not a pass" — both, and it is the same defect meeting them from two sides: the denominator is unstated *and* the subject is empty. It does not argue for the other five.

_Provenance: first-party observation by the unattended sweep of 2026-08-27 of its own `ost_next_work` response, plus `ost_read_repo` reads of `src/mcp/next-work.ts` and `src/ost/ageing.ts`. Not an ingested record — this session has not ended, so there is no transcript id to cite, and citing one for an unfinished session is the fault flagged elsewhere in this vault. Agent self-observation: it grounds feasibility and usability, not demand. No test was run, no result recorded, and this node's rung is unchanged._
