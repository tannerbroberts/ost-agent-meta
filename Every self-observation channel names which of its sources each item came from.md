---
type: Solution
status: shipped
source: 'TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

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
