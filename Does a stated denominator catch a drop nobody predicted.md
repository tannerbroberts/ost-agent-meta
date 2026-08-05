---
type: AssumptionTest
status: unvalidated
evidence: assertion
instrument: npx vitest run test/ost/census-drop-history.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**The assumption.** That reporting a denominator catches failures *nobody anticipated* -- which is the entire claim that ranked this above building another guard. A guard catches the failure its author imagined; a denominator is supposed to catch the ones they did not.

**Why it can still be wrong.** The denominator was built from a remembered failure (the em-dash sweep), and it is tested against planted instances of failures I could think of. Both of those only demonstrate it catches what was already imagined -- exactly the property it was supposed to improve on. The claim is unproven by construction until an unanticipated drop actually shows up in it.

**How it gets tested.** By reading `check` and `status` output across the next several firings, in both vaults, and recording every time the census line is non-empty:

- how many firings printed a drop, an unreadable file, or a git discrepancy
- for each, whether anyone had predicted that specific failure mode beforehand
- whether the named file led to a repair, or was noted and ignored

**Pre-committed threshold, fixed before the test runs.** Over the next **10 firings**: **one or more drops surfaced that nobody had predicted, each naming a file specific enough to act on**, validates the claim. **Zero non-empty census lines across 10 firings** does NOT validate it and must not be recorded as success -- it means the vaults were clean and the instrument is untested, which is a different thing from working. **A drop surfaced but ignored for 2+ consecutive firings** falsifies the operator-facing half: the number was printed and changed nothing, which makes it decoration.

**The failure mode I most expect.** That it fires only on vaults I broke myself while testing it, and never on a real one -- in which case it is an instrument that only its author can trigger.

**What it cannot tell anyone.** Whether the counts were right *before* this shipped. Every historical number in both vaults was taken over an unstated denominator and none of them can be retro-fitted; if something was being silently dropped last month, this cannot say so.

**Lane: compute-only** (prose, not a label; a human runs `ost-agent lane` to make it one). It reads output this loop already produces and needs no participant.

## History
- 2026-07-27 evidence: (none) → assertion — Agent-ideated from the shipped solution it tests. No result recorded yet by construction — it is designed to be read across 10 firings.
- 2026-08-05 instrument: (none) → npx vitest run test/ost/census-drop-history.test.ts — Asserts a census-history reader exists that accumulates every non-empty census line across the last 10 firings and names, per firing, the dropped or unreadable file specific enough to act on — the data this test's own threshold is counted over. Red today because nothing accumulates it: readTreeCensus() and reconcileWithGit() print their counts per invocation and the result is discarded, so there is no per-firing record for a spec to read and no exported reader to import.
