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
