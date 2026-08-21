---
type: Opportunity
source: 'agent-observation:2026-08-21-unattended-sweep'
created: '2026-08-21'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion

**The need, from the side of whoever works the hygiene list.** When I look at a flag, apply the judgement it asks for, and write that judgement on the node it sits on, the flag should stay cleared — or come back only when the facts behind it change. Instead the same twelve extent flags returned on 2026-08-11, 2026-08-17, 2026-08-19, 2026-08-20 and again on 2026-08-21, each time already carrying a prior pass's reasoned DISTINCT verdict in its own `## Issues`, and each pass spent its hygiene budget re-reading verdicts it could not act on.

**The mechanism, verified against the code this pass rather than inferred.** The clear exists. `src/ost/extent.ts` states in its own header that "an annotation clears an issue a session judged false, exactly as with every other hygiene rule", and `test/ost/extent.test.ts` pins the integration end to end: `ost_annotate({ title, issue })` with the flag's *exact* issue string makes the flag disappear from the next `computeNextWork` and lets `done` flip. What none of the four passes did was quote that string. Each wrote the verdict in its own words — "shared-extent flag vs X adjudicated by Torres's interventional test: DISTINCT, do not merge …" — which is the right content and the wrong key. Nothing on the surface says the key is the text: the issue string itself ends "merge with ost_merge_nodes, or rewrite each from its own evidence" and never mentions annotating; the `ost_annotate` description says "flag orphans, dangling links, or likely duplicates", not "repeat this text to clear". So four passes reached for the sanctioned mechanism, missed it by wording, and concluded that "the extent-detector has no memory of prior adjudications" (recorded on "A human re-judges the first twelve extent flags against Torres's test", 2026-08-19) — a wrong diagnosis the tool's silence made reasonable, and one that recommended building a verdict store the product already has.

**What it cost.** Twelve flags times four passes of re-adjudication; three nodes each carrying three near-identical verdict paragraphs; one standing human ask ("A human re-judges the first twelve extent flags") partly motivated by churn rather than by doubt about any verdict.

**Repaired for these twelve this pass** by annotating each flagged node with its exact issue string, beside the reasoned verdict already there. The need is about the *next* flag: a pass meeting a new extent flag tomorrow holds exactly the instructions the last four held.

**Litmus — is there more than one way to address it?** Yes: say the key in the issue text; match a prior annotation by rule and sibling instead of by whole string; let the scanner read verdict prose; or route verdicts through the typed suppression ledger that already exists. These disagree about who may clear a flag and about what a clear should survive, so this is a need, not a solution in disguise.

**Distinct from its siblings under this parent.** The siblings are about facts the queue already holds and ignores — `status: shipped`, `status: deferred`, "this is a category". This is the reverse: a clear the queue *honours* but the pass cannot discover. Dropping shipped nodes from the instrument queue does nothing here; a discoverable clearing key does nothing for shipped nodes.

**Provenance.** First-party observation of this product's tool output and source (`src/ost/extent.ts`, `test/ost/extent.test.ts`) across five unattended sweeps; no outside operator has reported it. Floor rung on purpose.
