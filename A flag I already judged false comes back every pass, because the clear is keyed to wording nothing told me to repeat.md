---
type: Opportunity
source: 'agent-observation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[The extent flag's own text names the annotation that clears it, beside merge and rewrite]]
[[The scanner matches a prior annotation by rule and sibling, not by whole string, so a written verdict that names the pair clears it]]
[[Extent verdicts go through the typed suppression ledger, holding while both siblings' extents are unchanged]]

**The need, from the side of whoever works the hygiene list.** When I look at a flag, apply the judgement it asks for, and write that judgement on the node it sits on, the flag should stay cleared — or come back only when the facts behind it change. Instead the same twelve extent flags returned on 2026-08-11, 2026-08-17, 2026-08-19, 2026-08-20 and again on 2026-08-21, each time already carrying a prior pass's reasoned DISTINCT verdict in its own `## Issues`, and each pass spent its hygiene budget re-reading verdicts it could not act on.

**The mechanism, verified against the code this pass rather than inferred.** The clear exists. `src/ost/extent.ts` states in its own header that "an annotation clears an issue a session judged false, exactly as with every other hygiene rule", and `test/ost/extent.test.ts` pins the integration end to end: `ost_annotate({ title, issue })` with the flag's *exact* issue string makes the flag disappear from the next `computeNextWork` and lets `done` flip. What none of the four passes did was quote that string. Each wrote the verdict in its own words — "shared-extent flag vs X adjudicated by Torres's interventional test: DISTINCT, do not merge …" — which is the right content and the wrong key. Nothing on the surface says the key is the text: the issue string itself ends "merge with ost_merge_nodes, or rewrite each from its own evidence" and never mentions annotating; the `ost_annotate` description says "flag orphans, dangling links, or likely duplicates", not "repeat this text to clear". So four passes reached for the sanctioned mechanism, missed it by wording, and concluded that "the extent-detector has no memory of prior adjudications" (recorded on "A human re-judges the first twelve extent flags against Torres's test", 2026-08-19) — a wrong diagnosis the tool's silence made reasonable, and one that recommended building a verdict store the product already has.

**What it cost.** Twelve flags times four passes of re-adjudication; three nodes each carrying three near-identical verdict paragraphs; one standing human ask ("A human re-judges the first twelve extent flags") partly motivated by churn rather than by doubt about any verdict.

**Repaired for these twelve this pass** by annotating each flagged node with its exact issue string, beside the reasoned verdict already there. The need is about the *next* flag: a pass meeting a new extent flag tomorrow holds exactly the instructions the last four held.

**Litmus — is there more than one way to address it?** Yes: say the key in the issue text; match a prior annotation by rule and sibling instead of by whole string; let the scanner read verdict prose; or route verdicts through the typed suppression ledger that already exists. These disagree about who may clear a flag and about what a clear should survive, so this is a need, not a solution in disguise.

**Distinct from its siblings under this parent.** The siblings are about facts the queue already holds and ignores — `status: shipped`, `status: deferred`, "this is a category". This is the reverse: a clear the queue *honours* but the pass cannot discover. Dropping shipped nodes from the instrument queue does nothing here; a discoverable clearing key does nothing for shipped nodes.

**Provenance.** First-party observation of this product's tool output and source (`src/ost/extent.ts`, `test/ost/extent.test.ts`) across five unattended sweeps; no outside operator has reported it. Floor rung on purpose.

## The key is stricter than "quote the exact string", and this pass proved it by clearing two flags (2026-08-23 unattended sweep, repo sight held)

The diagnosis above is right and incomplete. It says four passes "missed it by wording" because each wrote the verdict in its own words. This pass found the next layer: **quoting the exact issue string is not sufficient either — anything appended to the same annotation bullet defeats the clear.** That matters because the repair the node records as done was written in the defeating form.

**What was on the tree this morning.** Both flagged nodes carried a bullet containing the flag's exact issue string, followed by a verdict:

`- 2026-08-23 subset evidence extent: … or cite the evidence that makes it a genuinely separate need. ADJUDICATED 2026-08-23: DISTINCT — see the dated verdict above; do not re-hang.`

The issue string is present verbatim. The flag was reported anyway, on this sweep and the one before it.

**What cleared it.** One `ost_annotate` per node carrying the issue string and *nothing else* — no date, no verdict, no trailing sentence. `ost_next_work` went from two `hygieneIssues` to `hygieneIssues: []` in the same pass, with no other change to either node. The two flags were "shared evidence extent" on "The session tries to write a file before it has read it this run, and the guard fails the turn instead of reading first" and "subset evidence extent" on "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed".

So the annotation is matched as a whole value, not scanned for a substring. A leading date is tolerated (the writer adds one and the shipped spec `test/ost/extent.test.ts` passes with it); a trailing anything is not.

**Why this compounds rather than merely adding a detail.** Two mechanisms interact, and each hides the other:

1. A pass that reads the flag, applies Torres's test and writes the verdict *onto the same bullet* produces something that looks maximally correct — the machine's exact words plus the reasoning a human would want — and clears nothing.
2. `ost_edit_node` consolidation drops the clean marker. Both nodes record that their 2026-08-23 consolidation removed the bullet that had been suppressing the re-report. A body rewrite is exactly what a pass does when a node has grown too long, so the tidying step silently re-arms every flag the node had cleared.

Together they explain the whole recurrence history without anyone having judged a flag wrongly: the verdicts were right every time, and the mechanism for recording them was never the mechanism that clears them.

**The form that works, for whoever meets the next flag.** Two separate writes. First `ost_annotate` with the issue string exactly as `ost_next_work` printed it and nothing appended — that is the key, and it is not prose for a human. Then put the reasoned verdict wherever it belongs as its own bullet or section. Keeping them apart is what makes the clear survive; merging them is what has cost five passes.

**What this does not settle.** Whether the extent verdicts themselves are right is still the open human ask "A human re-judges the first twelve extent flags against Torres's test", and nothing here touches it — this pass re-applied clears for verdicts three earlier passes had already argued, and argued identically. Also untouched: a clear keyed to the whole string still breaks whenever the record counts embedded in it change, which is the durability question the sibling "Extent verdicts go through the typed suppression ledger, holding while both siblings' extents are unchanged" is about. This finding sharpens the diagnosis; it does not choose between the four solutions above it.

_Method: first-party read of `src/ost/extent.ts` and `test/ost/extent.test.ts` via `ost_read_repo`, plus an observed before/after on this vault's own `ost_next_work` in a single pass. The before/after is an observation of tool behaviour, not a recorded test result — no `## Results` was written and no rung moved._

## Issues
- 2026-09-17 2026-09-17 unattended sweep (repo sight held) — a second instance of this need, in a different bucket and with a different clearing mechanism. Recorded here rather than as a new node because the need statement above already covers it.

THE OBSERVATION. `solutionsMissingInstruments` reported 75 entries this pass. Four were opened — "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target", "Name the engine's published dialect in the tool description and build no validator of our own", "Group the queue by error signature at read time, and change nothing on disk", and "A dead-man's-switch outside the host, because an in-host watchdog dies with the host" — and all four declare in their own prose that the single test beneath them is humans-required on purpose: the belief is desirability or viability about people outside this building, an exit code cannot observe it, and an instrument written there could only measure that our code emitted something. Three of the four already carry an explicit prior instrument-census note saying exactly that (2026-09-07, 2026-09-16, and the evidence-window node across five firings), each naming the same remedy — `ost-agent lane --set`. The fourth declares it in its Definition of done and had never been censused.

WHY THIS IS THIS NEED AND NOT A NEW ONE. The judgement was applied and written on the node it sits on, and the bucket re-reports it anyway. The difference from the extent case above is only the key: there the clear existed on the surface and was missed by wording; here the clear is off the unattended surface entirely, because `ost_flag_humans_required` is withheld from this pass on purpose and `ost-agent lane --set` is a human's. Same shape, opposite cause.

WHAT IS NEW IN AGGREGATE, WHICH IS THE PART WORTH KEEPING. No node holds the count. Four nodes each say "a human should set the lane" and nothing sums them, so every firing meets 75 undifferentiated entries and pays per-node reads to separate the already-adjudicated from the genuinely un-done — this pass spent four such reads before finding the prior notes. The product ships two mechanisms that would record the judgement where the sweep reads it: the lane label, and `ost-agent dispose`, whose own spec fixture reason for the `opportunity` kind is an under-served counter that is not a gap. Both are unused here — this pass's sweep reports `withheldByDisposition: []`, so no subject of any kind has ever been settled in this vault's ledger. Unused rather than weighed and rejected, which is a different fact.

WHAT WOULD SETTLE IT, for whoever holds a shell: `ost-agent lane --set` on those four titles, or one disposition per node. Either takes them off every future firing's census instead of leaving each firing to re-derive the same verdict.

LIMITS. Four of 75 were opened, chosen as the entries most mechanism-shaped and therefore most likely to be genuinely instrumentable — that biases the sample against the humans-required finding rather than for it, but it is four of four and not a rate over the bucket. Fifty of the 75 sit behind the response cap and were never visible to this pass at all. Whether each of those four verdicts is correct was not re-litigated; this pass read them and agreed. Nothing was executed, no instrument set, no rung moved, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.
- 2026-09-18 2026-09-17 unattended sweep (second firing of the day, repo sight held) — extends the census in the entry above by two nodes and adds one decline class it does not have. Deliberately NOT a restatement: that entry's finding, its remedy and its limits all stand unchanged and are not repeated here.

TWO MORE, SAME VERDICT. This firing opened "Append-only tool surface with no delete or shell tool" and "Axioms elicited at the moment a derivation needs them, one accept-or-reject ask at a time", neither of which the earlier entry sampled. Both decline for reasons already written on themselves — the second carries a 2026-08-29 instrument-census note naming `ost-agent lane --set` as the remedy, the same remedy the other four name. With the four above, that is SIX of six opened, from two independently chosen samples on the same day, every one already adjudicated. Still not a rate over the bucket: 50 of the 75 sit behind the response cap and have never been visible to any firing.

THE NEW CLASS, WHICH IS THE PART WORTH KEEPING. The five other nodes decline because an instrument there would be USELESS — an exit code cannot observe a person's desirability or viability judgement. "Append-only tool surface with no delete or shell tool" declines because an instrument there would be HARMFUL, and it reasons it out in its own prose: a spec asserting "no delete tool" would go red today, which looks like a valid red and is not one, because it would be measuring the absence of a feature that was added deliberately — `ost_edit_node`, `ost_detach_nodes` and `ost_merge_nodes` all ship — and a builder could pick the red up and implement it. Seven passes have declined on that reasoning. That distinction matters for anyone draining this bucket mechanically: the useless kind is safely left alone, and the harmful kind must not be instrumented even by a pass that decides to clear the count. A lane label does not capture it either, since the node's open question is not who runs the test but whether the claim still describes the product — the node asks a human to rule it (a) superseded or (b) a live alternative, and that ask is eight passes old.

WHY THIS IS THE SAME NEED. Unchanged: the judgement was applied, written on the node it sits on, and the bucket re-reports it anyway, because the clear is off this surface. The only thing six-of-six adds to four-of-four is that two independent samples drawn hours apart hit the same wall, which makes it a property of the bucket rather than of either sample.

CORROBORATION NOW ON THE TREE. `USAGE:2026-09-17` was captured at this firing's ingest and recorded on "A third of my calls go on re-asking what is outstanding": 305 calls across 22 sessions produced 5 writes (1.6%), with `ost_create_node` and `ost_set_instrument` both at ZERO for the day. That is this need's cost measured mechanically for the first time — 22 firings re-deriving verdicts the tree already held, and clearing nothing.

LIMITS. Six of 75 opened, chosen for being mechanism-shaped and therefore biased against this finding rather than for it. The (a)/(b) question on the append-only node was read and not answered — it is a human's. Nothing was executed, no instrument set, no rung moved, no status changed, no node created. `ost_check` is withheld on this surface, so this write is unverified by the invariant checker by design.
