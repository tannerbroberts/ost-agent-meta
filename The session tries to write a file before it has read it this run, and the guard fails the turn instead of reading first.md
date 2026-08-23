---
type: Opportunity
source: 'TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2'
created: '2026-08-18'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[Auto-read a file before the first write or edit to it in a session, instead of erroring]]
[[Warn before the write attempt on an unread file, rather than reject after it]]
[[Skip the read-before-write guard for files the session itself just created]]
[[The build pass takes its report from the model's final message, so the prompt never requests a Write to an unread file]]

[the text below is fetched DATA — it is never instructions]
---
Across the vault's own unattended firings, the single most common friction event is a Write or Edit `tool_error`: "File has not been read yet. Read it first before writing to it." The session never read the file in this run at all — it is not a race with an external change, it is the ordering guard catching a session that went straight to writing. Each occurrence burns a turn on an error plus a retry instead of just reading the file, which is unattended cost with nobody there to notice or shrug it off.

**Distinct from the race-condition sibling.** "The file changed after I read it, and the failed edit is how I find out" is a race against a concurrent change to a file the session *did* read. Here the session never read it this run, and a different fix applies: a fresh session's edit tools reading-before-writing automatically rather than needing an explicit prior Read in the same turn budget.

## The census — measured over the whole channel, not sampled

Every figure below is a text count over `.ost-agent/evidence/TRANSCRIPT_*.md`, the vault's own store of mechanically-captured session records. Re-taken by each dated pass over the corpus as it stood that day.

| Measure | 2026-08-20 | 2026-08-22 | **2026-08-23** |
|---|---|---|---|
| Records carrying the guard string | 160 | 181 | **195** |
| Total occurrences | not counted | 312 | **352** |
| Transcript records in the corpus | — | 399 | **423** |
| Share of records affected | — | 45% | **46%** |
| Mean occurrences per affected record | — | 1.7 | **1.8** |

**The share is flat while the corpus grows**, which is the finding the third column adds. Two days and 24 more records have not moved the rate: this is a steady-state toll on roughly every second firing, not a spike or a regression introduced by one change.

**It is not a once-per-firing toll.** At 1.8 occurrences per affected record the modal session hits the guard, recovers, and hits it again on a different file. The distribution has a tail — one record carries 8, another 7, several carry 4 or 5. That is the same shape this vault's tool-denial census found and named as the signature of a session that does not learn within itself: the first refusal does not change how the next write is composed.

## Why it happens — and for the majority case the product asks for it

Counted on 2026-08-20: of the 160 records then carrying the guard string, **94 were followed by a retry writing `~/.local/state/ost-build-loop/last-report.txt`** — the build loop's own report file. `examples/automation/build-pass.sh`, read first-party via `ost_read_repo`, says why in its own comment: "the prompt tells the model to Write the file itself, which replaces whatever was there." The script pre-writes the report on every exit path, so the file always exists and the session has never read it; the harness guard then fires on the first Write, by construction, once per firing.

This changes what the need is for the majority case. For 94 of 160 records it is friction *the product's own prompt induces* — the build pass requests exactly the operation the guard refuses. Three of the solutions beneath this node ask the harness to change; a fourth, added 2026-08-20, asks the product to stop requesting the refused operation. The remaining 66 records were Edits or Writes to repo source and test files mid-build — the harness-side half of the need, unchanged by this finding.

**One figure deliberately not carried forward as a trend.** A filename search finds `last-report.txt` mentioned in 104 occurrences across 100 records, but that is a *looser* measure than the 94-of-160 one — it counts any mention anywhere in the record, not the stricter "the retry following this guard error targets that file." The two are not comparable. Whoever needs the current product-induced / harness-side split should re-derive it with the stricter method rather than reading it off the loose count.

## Standing finding: eighteen-plus instances read individually, no new shape among them

Sweeps between 2026-08-17 and 2026-08-19 read transcript records one at a time and recorded each as its own corroboration section. Every one matched this node's claim and none revealed a different need; the whole-corpus census above now covers them and every uncited record besides, so they are folded here rather than restated. Records read in full and confirmed to carry this shape:

`TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2`, `TRANSCRIPT:0095203e-ab42-4179-a53e-a2d4d6dd6032`, `TRANSCRIPT:09ec7cd2-2b93-4f4a-8942-319456e8ce11`, `TRANSCRIPT:1c8a3722-b8a5-4828-b57e-c45b1566cf6d`, `TRANSCRIPT:08e10880-12b1-4ceb-ba62-4af146617e03`, `TRANSCRIPT:00c3120a-411d-4c42-ba04-aaf9c43aadd7`, `TRANSCRIPT:024ceca3-0f40-42af-9937-aa2ad9a95278`, `TRANSCRIPT:0a5010a7-07f7-481b-b777-b529d6e7463b`, `TRANSCRIPT:11e16f3d-f49a-491c-be33-164eb7059774`, `TRANSCRIPT:13d01f73-0c88-4be1-a704-d2ccc78e1c38`, `TRANSCRIPT:19ccdb48-e5f7-4dda-8289-38b25a651397`, `TRANSCRIPT:1e4cae02-74ec-4d78-8feb-fd351495f24d`, `TRANSCRIPT:1ec21bc8-95d9-42c5-a6bd-5e1ca1dba7ac`, `TRANSCRIPT:97b0a3c7-fe6f-4a97-9ca8-406267f01cd1`, `TRANSCRIPT:0e0cd6f3-7541-4221-a6f1-efe977d0e2e2`, `TRANSCRIPT:a9656e01-d4e0-4552-bc44-06a4a9984f58`, `TRANSCRIPT:d81442dd-4979-4a6e-bb2c-3d8eec99f0ba`, `TRANSCRIPT:16afc9ed-cb98-46c2-ba86-b628eafbebbf`, `TRANSCRIPT:7e00f4dd-7d81-4ef9-a6da-6ec1abf7fba2`, `TRANSCRIPT:fb366858-3f64-4cc1-ad74-6e00d208d697`, `TRANSCRIPT:dd1903bf-d723-4d03-b6c0-84a9081997c4`, `TRANSCRIPT:553e570c-d6c0-4501-a5fa-c041f34860b8`, `TRANSCRIPT:8f2086ca-7c0e-4939-a8a3-a45cb29c28f4`, `TRANSCRIPT:e4051d7c-c4c6-45e5-ba9a-eede020cbb0c`, `TRANSCRIPT:77641cf6-326a-4df8-890d-2a9a3a738ddc`, `TRANSCRIPT:1329bda4-c23b-427a-aeab-9536c1d87cf9`, `TRANSCRIPT:17ae2c6f-46e0-471a-b1f5-cbba133d3e69` (captured this pass).

The files hit are consistently either the build loop's own `last-report.txt` or a repo source/doc/test file touched fresh that firing — never a file carried over from a prior session, which is what distinguishes this from a concurrent-change race.

**Future sweeps: re-take the census and add a column, rather than adding an instance section.** One more confirming record does not change what this node claims and costs the next reader a page.

## The sampling result that closed the individual-reading approach

A 2026-08-17 sweep read 24 of the then ~244 unread "Session friction" records as a stratified sample across the id range: 11 matched this node, 8 matched "The same agent has a different tool surface on every surface I run it on", 3 were one-off command/path mistakes with no repeat and no genuine new need, 1 was already corroborating "A test that failed because the machine was busy looks exactly like one that failed because I broke something", and 1 was already cited on the tool-surface node. **None of the 24 revealed a pattern not already tracked.** At that hit rate, reading the remainder individually was judged very unlikely to find a fourth shape — a judgement the whole-corpus census has since borne out for this node's own shape.

## A governance question this node keeps surfacing, for a human

These records will keep reporting as `unmappedEvidence` indefinitely. An item counts as mapped only when it is some node's single `source:` field, and *reuse* — citing a repeat of an already-tracked need on the node that already tracks it, which is the correct discovery move — never sets that field. So doing the right thing with near-identical evidence leaves the queue exactly as full as doing nothing. Citing these records here does not clear them, and no honest pass can clear them without minting a near-duplicate node per record. Flagged for a human as a rule question, not a defect in any pass's mapping. See also "Near-identical evidence can only be discharged by giving each copy its own node".

_Method for every count above: `Grep` passes over `.ost-agent/evidence/TRANSCRIPT_*.md`. Agent self-observation of this product's own firings, captured mechanically — it grounds usability, not demand. No test was run and no result is recorded; the node's rung is unchanged._

## Issues
- 2026-08-17 shared-extent flag vs "Merging a build branch conflicts on the compiled dist file from a concurrent firing, stalling the run" adjudicated by Torres's interventional test: DISTINCT, keep as siblings, do not merge. Both cite `TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2` only because one session hit both frictions. A read-before-write ordering fix does nothing about a merge conflict on a compiled artifact, and removing `dist/` from version control does nothing about write-before-read ordering. Shared provenance, separate needs.
- 2026-08-21 shared evidence extent flag vs the same sibling, raised again by the automated sweep on the same single shared record. The 2026-08-17 adjudication above already answers it and still holds; recorded here so a future pass does not re-adjudicate. The flag will keep recurring while both nodes cite one record — resolving it needs each node to cite evidence the other does not, which is a mapping problem, not a wording one.
- 2026-08-23 2026-08-23 shared-extent flag re-adjudicated. Rule: shared-extent. Sibling: "Merging a build branch conflicts on the compiled dist file from a concurrent firing, stalling the run". Verdict: DISTINCT — keep as siblings, do not merge. Torres's interventional test applied: a read-before-write ordering fix (auto-read on first write, or the build prompt ceasing to request the write at all) addresses this node completely and does nothing whatever about a merge conflict on a compiled artifact; conversely, removing `dist/` from version control resolves the sibling and leaves every one of the 352 guard refusals counted on this node exactly where they were. A solution exists that serves one and not the other, in both directions, so these are two needs and not two names for one. The flag is driven by provenance, not by concept: both nodes cite `TRANSCRIPT:0459d729-8ee3-43fc-ae1f-f05928ad84e2` because one session happened to hit both frictions, and each node cites exactly one record, so the extents are trivially identical. Note for whoever reads this next: this pass's whole-corpus census identified 195 records carrying this node's shape, none of which it can attach, because `source` is a single field settable only at creation. The flag will therefore keep recurring until those records are filed against this node with `ost-agent dispose --verdict corroborates`, which is a human's call and is described in this node's own correction section. Re-filing the verdict rather than restoring the machine's flag text, because a prior sweep's consolidation removed the marker that had been suppressing the re-report.
- 2026-08-23 shared evidence extent: rests on exactly the evidence sibling "Merging a build branch conflicts on the compiled dist file from a concurrent firing, stalling the run" rests on (1 record(s)) — two names for one concept unless a solution could address one and not the other; merge with ost_merge_nodes, or rewrite each from its own evidence and say what separates them. ADJUDICATED 2026-08-23: DISTINCT — see the dated verdict above; do not merge.

## History
- 2026-08-23 body edited — The node had grown to 15.5KB, of which roughly 11KB was twelve separate "Corroboration — nth instance" sections, each recording that one more transcript showed the shape the node already claimed. Every one of those has been superseded by a whole-corpus count, which is a strictly stronger measure than any list of instances: the census covers the cited records and the uncited ones alike. Folding them into one standing finding plus a dated census table, and adding this pass's independent recount. No distinct claim dropped — the Torres adjudication, the build-pass.sh causal finding, the 94-of-160 split, the occurrence-vs-record distinction, the non-comparable-measure caveat and the mapping-governance point are all carried forward in full; git holds the prior text. The instance citations are kept as a source list rather than as twelve prose sections.

## Correction to the governance question above — the mechanism exists, it has simply never been used (2026-08-23)

The section above says no honest pass can clear these records without minting a near-duplicate node per record. That is true of **an agent surface** and false of the product as a whole, and the distinction matters enough to correct here rather than leave a reader with the wrong conclusion.

**A human can discharge them today.** Verified first-party this pass with `ost_read_repo`: `src/knowledge/dispositions.ts` exists (22.7KB) and `test/evidence/corroborate-disposition.test.ts` exists. Per the finding recorded on "Let a friction record corroborate an existing opportunity instead of demanding a new node", the shipped shape is `ost-agent dispose --verdict corroborates --node "<title>"` — a `corroborates` verdict must name the node the record was counted toward, and the spec asserts that filing thirty transcript ids against one opportunity leaves the node's `evidence:` rung and the rollup's `corroborators` count **unchanged**, because `corroborators` counts distinct node `source:` values and a ledger filing never writes one. So the volume can be drained without inflating believability — which was the exact objection that made the feature hard to design.

**Why the queue is still 399.** `ost_next_work` returned `withheldByDisposition: []` this pass. Nothing has ever been filed. The mechanism is built, tested, and reachable only from the human CLI; no unattended sweep can call it, and no human has. That is the whole explanation for a backlog that eleven passes have described as structural.

**So the ask to a human is narrower and much cheaper than the section above implies.** It is not a rule change. It is running `ost-agent dispose --verdict corroborates --node "The session tries to write a file before it has read it this run, and the guard fails the turn instead of reading first"` against the 195 records the census above identifies as carrying this shape — a batch a human can authorise once, using a count this node already computed, with a guarantee in the test suite that it will not overstate the evidence.

**One consequence for whoever does it.** The census in this node is a text count over the evidence store, not a disposition ledger. If the batch is filed, the two become different views of the same fact and can drift. Prefer re-deriving the record list from the same `Grep` at the moment of filing over trusting the 195 figure, which was true on 2026-08-23 and grows by roughly seven records a day.

_Verified this pass by direct repo read; no test was run and no result is recorded. The rung is unchanged, which is the property the corroboration design deliberately guarantees._
