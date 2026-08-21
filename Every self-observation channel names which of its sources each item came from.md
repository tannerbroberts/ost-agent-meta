---
type: Solution
status: shipped
source: 'TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Every channel can name a per-item source, not just a per-channel one]]

**The failure this closes, measured before it was fixed.** The transcript channel — the one whose entire premise is "the agent is this product's most active user" — had never once read an unattended firing. Claude Code keys a session directory to the cwd a session ran in; a firing runs with cwd set to the *vault*, while `adapters.transcript.projectDir` pointed at the *code repository*. Counted on this vault on 2026-08-06: **36 distinct sessions cited across 114 nodes, all 36 from the code repository's directory, zero from the directory holding 100 firings.**

So every piece of "the agent's own usage" evidence in this tree describes the agent *being built by a person*, and none of it describes the agent *running by itself* — which is the half the outcome mandate actually asks about, since an observed self-failure is the thing that outranks everything else here.

**Why nothing reported it.** The channel was neither disabled, nor unavailable, nor undated, nor silent. Its cursor advanced, items arrived every pass, and by every state `ost-agent channels` can report it was healthy. There is no word in that vocabulary for **healthy and half-blind**, and that is the general defect: a channel that reads one of its two sources looks identical to one that reads both.

**What shipped (2026-08-06).** `TranscriptSource` takes a list of directories scanned as one newest-first pool, and `transcriptDirs` composes it from what the vault already declares — the configured project, plus `loop.spend.sessionsDir`, which the operator wrote down once for the spend ceiling. No second declaration was added, on the same argument `src/loop/corrections.ts` makes for reusing it: a key somebody has to type twice is a key they leave unset, which would have turned this off on exactly the vaults that run unattended.

**The part that is the actual idea, and is worth more than the bug fix.** Each evidence item now names the source it came from, and that label is required rather than defaulted. Merging two piles unlabelled would make them indistinguishable downstream — every item is `TRANSCRIPT:<uuid>`, and a uuid does not say whether anyone was watching. Friction in an attended session is something a person could have fixed on the spot; identical friction in an unattended firing is a failure mode nobody saw. Those are different findings and the tree should never have to guess which it is holding.

**What this does NOT establish.** That the firing sessions contain anything worth reading. The channel now sees them; whether an unattended firing's friction distils into opportunities a human agrees with is unmeasured, and is the same open question its attended half already carries.

## Definition of done

Met. `test/adapters/transcript.test.ts` (both piles harvested, origin carried and not cross-contaminated, a missing directory not cancelling a present one, the newest-first cap spent across directories rather than per directory, one id harvested once) and `test/runner/context.test.ts` (a session in the declared `sessionsDir` becomes evidence labelled unattended, the path declared exactly once, a vault with no `loop:` block unchanged). Recorded as `shipped` rather than carrying a red instrument, because a spec asserting shipped behaviour would pass on arrival and give a builder no definition of done.

## The next measurement, when there is one

The first firing after this landed is the first unattended session this tree has ever been able to read. Whether it yields an opportunity nobody had already filed by hand is the number that says whether this earned its keep.

## Issues
- 2026-08-06 unresolved-citation (flagged by ost_check): frontmatter cites `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, and no record under `.ost-agent/evidence/` carries that id. Same fault, same missing id, on four nodes created in one sitting; the full diagnosis and the check that would settle it are recorded on "A guard derived the rule it was checking, so it agreed with the bug for 23 releases". Sharper here than on the siblings: this node's whole claim is that every self-observation channel should name where each item came from, and its own provenance points at a record that does not exist. Until it is settled, treat its evidence rung as unsupported.

## Definition of done

"Refuse a source that names no record, at write time rather than at sweep time"

```
npx vitest run test/adapters/source-attribution.test.ts
```

Red today, and red for a reason stronger than a missing file: this node itself cites `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, which resolves to nothing, and the write that created it was accepted. The spec's second half replays exactly that write and requires a refusal. A builder can watch the current behaviour fail before writing a line.

Green here proves sources resolve. It does not prove they are the right sources, and it says nothing about whether finer attribution improves the tree — that needs an operator who has worked with both.

## The broken-citation fault has a mechanism, and it was watched closing

Earlier in this pass, four nodes — this one among them — carried an `unresolved-citation` hygiene issue: each cited `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, and no stored evidence record had that id. The diagnosis written into the `## Issues` sections was that the pass had cited the session it was running in, which the transcript adapter cannot have stored yet because that session had not ended.

That diagnosis is now confirmed by observation rather than argument. The third `ost_ingest_inbox` of this pass captured sixteen records, and the first name in the list was `Session friction 89ac8277-29ce-4d80-827e-cefea0bebabf`. The next `ost_next_work` returned `hygieneIssues: []`. Four violations cleared at once, by an ingest, with nobody repairing anything.

So the fault is real but temporary, and its shape matters more than its severity: **a node that cites its own live session is born with a broken citation and self-heals whenever that session is next harvested.** Between those two moments the tree fails `ost_check`, and there is no way to tell, from the violation alone, whether it is a citation that will resolve itself tonight or one that names a record that never existed. Those two want opposite responses — wait, or come down to `assertion` — and the check reports them identically.

Three things follow for this solution, which is about channels naming their sources.

Attribution is not only coarse, it is temporarily wrong by construction, and any design that treats a source string as immediately verifiable will mis-handle the commonest case in this vault.

A check that cannot distinguish "not yet harvested" from "does not exist" produces a violation an operator learns to wait out, which is how a real broken citation gets ignored. The sibling assumption test "Refuse a source that names no record, at write time rather than at sweep time" is now the wrong shape as written: refusing at write time would have refused all four of these nodes, and all four were correct. The refusal needs to distinguish an id that is well-formed and unharvested from one that is neither — and that distinction is checkable, because a live session id names a file that exists on disk before the adapter reads it.

Any humility about the ladder is warranted here. The four nodes rested on `observed` while pointing at nothing, for some hours, and nothing in the tree noticed except a rule that fires after the fact.

Provenance: this pass, 2026-08-06, first-party — the ingest and the cleared check were both observed directly.

## History
- 2026-08-21 status: shipped → shipped — Promotion to shipped recorded with reasoning so trustsShippedStatus (src/eval/shipped-audit.ts) stops reporting this node as instrument debt; its History carried no promotion line. Verified against the repository this pass via ost_read_repo directory listings: every file this node names outside a code fence exists — test/adapters/transcript.test.ts, test/runner/context.test.ts and src/loop/corrections.ts — which is the path-resolution half of the shipped audit (auditShippedSolutions), and the per-item `actor` stamp the idea describes is live in src/processes/tree.ts (writeEvidence takes `actor` as a separate argument and readEvidenceScan fails closed to `unknown`). The fenced test/adapters/source-attribution.test.ts is a definition of done for a follow-on and is excluded from the audit by design; it also exists now. Read, not run: the spec files were listed, not executed; no result recorded, not a validation.
