---
type: Solution
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[One ledger shape can carry a disposition for evidence, solutions and opportunities alike]]
[[An operator would accept a pass dismissing its own work list by written assertion]]

**The idea.** One append-only ledger of dispositions, written by a pass and read by every bucket. An entry names the item, the disposition, the reason, and the pass that wrote it — "this evidence corroborates a node the tree already has", "this solution ships", "this opportunity's solution space lives on its children". A bucket lists an item only if no live disposition covers it.

**Why the general form is worth its cost.** The three faces of this defect look like three bugs and are one absence: `ost_next_work` has no notion of "closed", so every bucket re-derives outstanding work from raw structure on every pass and each leaks differently. Both siblings fix one face by making the derivation smarter. Neither helps the next bucket to grow the same hole, and the evidence face cannot be fixed by a smarter derivation at all — "Evidence that fits no layer keeps coming back, so the pass never runs out of work" established by direct test that an item is mapped only when a node's frontmatter `source:` equals the id, that body citations are invisible to the sweep, and that no tool can add a `source:` to an existing node. There is nothing on disk for a cleverer predicate to read. Something has to be written.

**The constraint that node already discovered, which this design has to honour.** The acknowledgement must live somewhere the *sweep* reads, not somewhere a *reader* reads. A `## Disposition` section in a node body was tried and does not work. The ingest ledger, or a frontmatter field carrying ids, would.

**What it makes possible that neither sibling does.** A pass could finally be honestly done. Right now `done: true` is unreachable while 60 evidence items are permanently unmapped, so the loop's completion signal carries no information and the operator cannot use it to stop paying.

**Where it fails, and this is the serious one.** It hands the agent a way to make any work disappear by writing a sentence about it. Every other item on this list is removed by doing something checkable — shipping code, attaching a red instrument, creating a node. A disposition is removed by asserting. That is the same shape as the self-validation the whole tool surface is built to refuse, and it belongs to the party whose budget is spent by the work it would be dismissing. If this ships, the disposition write is the highest-risk write on the surface and probably wants the reserved-section treatment: legible, dated, attributed, and cheap for a human to audit in bulk.

**Cost.** A store, a write path, a read in every bucket, and a review surface so a human can see what a pass dismissed. Much the largest of the three.

⚠️ Unvalidated. Agent-ideated, and it is the candidate that most benefits the agent proposing it — discount accordingly.

## Definition of done

"Write one disposition of each of the three kinds through a single ledger schema"

```
npx vitest run test/ost/disposition-ledger-shape.test.ts
```

Green means one entry type carries all three dispositions and every bucket reads them through one shared call. The design constraint is already established and is not negotiable: the ledger must live where the *sweep* reads, not where a *reader* reads — a `## Disposition` section in a node body was tried on 2026-08-05 and the sweep did not see it.

Do not build this before "Show five operators a pass's dismissed-work list and ask whether they would have let it stand" has run. That test can kill this candidate outright, and it costs five conversations against a store, a write path, a read in every bucket, and an audit surface.

## 2026-09-09 — this candidate shipped, its spec asserts every claim in its own Definition of done, and this vault has never written a single entry

Four findings, all first-party this pass, and the last one is the operative one. This node's body is still written in the future tense about a thing that exists.

**1. It is built, and the spec is the one this node named.** `test/ost/disposition-ledger-shape.test.ts` reads whole and asserts, against the real `computeNextWork`, exactly what the Definition of done above demanded: one entry type round-trips all three kinds; every bucket reads through the single one-argument predicate `isDisposed(ledger, subject)`; a record filed under the WRONG kind still settles its subject, which is the load-bearing assertion for "one entry type" rather than three special cases sharing a name; a mangled ledger line fails open and surfaces MORE work; and every withheld item is named on the response that withheld it, with reason and author. A fourth bucket was added beyond the three this node scoped — a settled solution stops owing an instrument too, asserted as `solutionsMissingInstruments` containing the subject before the settle and not containing it after.

**2. The risk this node called "the serious one" was not mitigated — it was removed.** The body warns that a disposition "hands the agent a way to make any work disappear by writing a sentence about it", and asks for the reserved-section treatment: legible, dated, attributed, auditable in bulk. What shipped is stronger than what was asked for. The write is not on the agent surface at all. Per `test/cli/dispose.test.ts`, it sits on the CLI in a human's hands alongside `result` and `promote`, refuses a dismissal with no `--by` and one with no `--why` and writes no ledger file when it refuses, refuses a `--kind` outside the vocabulary, reverses with `--reopen` as a second append-only entry that leaves the original on file, and `ost-agent dispositions` lists every live dismissal dated and attributed. The party whose budget the work costs is the party who writes the sentence. That answers this node's own objection.

**3. One instruction on this node was not honoured, recorded neutrally.** The body ends: do not build this before "Show five operators a pass's dismissed-work list and ask whether they would have let it stand" has run, because that test can kill the candidate for the price of five conversations. It was built first. The desirability question is still open and is still worth asking — what changed is that it is now a question about a thing operators can be shown rather than described.

**4. The operative finding: the ledger on this vault is empty.** This pass's own `ost_next_work` response reports `withheldByDisposition: []` while reporting 661 unmapped evidence records, 75 solutions whose tests are prose only, and `done: false`. The mechanism built to close exactly those counters has never been used once here.

**What that costs, stated as the arithmetic rather than as an opinion.** This pass sampled 5 of the 75 solutions in `solutionsMissingInstruments` and read each in full. Five of five are non-clearable by any unattended pass, and each already documents why on itself: three carry a Definition of done that is humans-required on purpose and says so ("Group the queue by error signature at read time, and change nothing on disk"; "Hand the oversized body to the harness's own compaction and store nothing new"; "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target"), one is feasibility about a harness this repository's specs cannot reach ("A background task's own output directory is automatically readable by the Monitor call that started it"), and one has had seven consecutive passes decline to instrument it on the reasoned ground that no honest red exists for it as worded ("Append-only tool surface with no delete or shell tool"). That is a sample, not a census, and it is the strongest sample available: these were chosen as the entries most likely to be mechanically instrumentable, so the ones not sampled are if anything likelier to be non-clearable, not less.

**So the bucket is not a backlog, and every pass that has read it as one has been reading it wrong.** Each of those five was correctly judged, the judgement was written on the node, and the entry returned anyway — the same defect the opportunity "A flag I already judged false comes back every pass, because the clear is keyed to wording nothing told me to repeat" records for extent flags, appearing in a second bucket with a different clearing key. The difference is that here the key exists, is shipped, is auditable and is reversible, and nobody has turned it.

**What a human could do with it, with the commands.** For a solution whose test is deliberately humans-required: `ost-agent dispose "<title>" --kind solution --by <who> --why "test is humans-required on purpose; see its Definition of done"`. For an evidence record that repeats a need the tree already holds, the CLI carries a sharpened verdict for exactly this case rather than a bare dismissal: `ost-agent dispose "<id>" --kind evidence --corroborates "<the node it strengthens>" --by <who> --why "<one line>"`, or `--no-genuine-need` where it reveals none. Both are reversible with `--reopen`, both are listed by `ost-agent dispositions`, and both keep the item counted somewhere a reader sees rather than amnestying it.

**Why this bears on the outcome and not just on this node.** The spec contains a test named "a pass can finally be honestly done — the completion signal moves", whose comment states the purpose in this node's own words: `done: true` was unreachable while items no derivation can ever clear sat on the lists, so the loop's only stopping condition carried no information and the operator could not use it to stop paying. That is still the live condition on this vault, eleven days of firings later, with the fix sitting unused on disk.

**Limits, and they matter.** Nothing was executed: the spec was read, not run, so "shipped" here means the source and its assertions exist and are consistent with the Definition of done, not that the suite is green. Status was deliberately not moved to `shipped` for that reason — that call wants someone who can run it. The 5-of-75 figure is a sample and is labelled one throughout; no census was performed and none should be inferred. Whether an operator would accept a pass's dismissed-work list standing is untested and is this candidate's own open assumption, unchanged by anything here. No instrument was set, no rung moved, no status changed, no node created.

_Method: first-party `ost_read_repo` reads of `test/ost/disposition-ledger-shape.test.ts` and `test/cli/dispose.test.ts` in full, directory listings of `test/`, `test/ost/`, `test/cli/`, `test/config/` and `test/evidence/`, plus this pass's own `ost_next_work` response and full reads of five solution nodes. Observed structure of the product's own code and spec suite; it grounds feasibility, not desirability._
