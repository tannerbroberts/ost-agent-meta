---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-27'
created: '2026-08-27'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Dropping the envelope test admits the product's own refusals without admitting ordinary command failures]]

**Variation dimension: bought-vs-built. Position taken: adopt the discriminator that already exists, unchanged, and build nothing — the change is a deletion.**

`src/loop/corrections.ts` already contains a tested answer to "is this a correction or merely a failure": `splitRefusal` keeps a refusal only when it names a permitted form, and its docstring records the real messages it was tuned against, including the end-anchoring rule added after a guard quoting ninety lines of the caller's own source was read as advice. That function is the product's considered definition of its own unit, and it is already built.

Sitting in front of it is a second, cruder test that predates it:

    const GUARD_MARKER = /<tool_use_error>/;
    if (!GUARD_MARKER.test(body)) continue;

This candidate is to drop that line and let the existing function decide. Nothing new is authored; one guard is removed and an already-shipped one becomes load-bearing.

**Why the removal is defensible on the module's own reasoning.** The stated purpose of the marker is to separate a guard refusing a call's *shape* from a command that merely exited non-zero. But `splitRefusal` tests for that directly — a non-zero exit names no permitted form and is dropped — whereas the marker tests for something else entirely: whether the *harness* was the refuser. The two were never the same question, and on `ost_*` refusals they give opposite answers. The refusal that has now cost three firings, `"is not an instrument form. The allowed forms are: vitest-spec (npx vitest run <path>.test.ts)"`, would pass `splitRefusal` on its plain reading and is discarded before reaching it.

**Against its siblings.** The publish-the-grammar candidate prevents refusals but only ones statable in advance, and needs new machinery to stay honest. The record-at-source candidate needs a change at every refusal site and turns rejections into writes. This one is a one-line diff against committed code, which makes it far and away the cheapest to try and the cheapest to reverse — and correspondingly the least ambitious: it fixes the carrier's blindness and does nothing about the refusals themselves.

**Its distinctive failure mode, stated plainly, because it is exactly what the deleted line was defending.** Ordinary command failures whose text happens to carry a remedy cue — `use`, `must`, `instead`, `try` — become ledger entries. The module's own docstring names a real instance of this going wrong. `splitRefusal`'s end-anchoring rule was the fix for that instance and is the reason to think the marker is now redundant belt-and-braces rather than the only thing holding the line; but "now redundant" is a claim about how well that rule generalises, and it is the claim this candidate is betting on. If it is wrong, the ledger gets noisier, and a ledger's entire value is being short enough to read.

**Sequencing note.** This is the cheapest of the three to build and the only one that can be evaluated against evidence already on disk — 588 harvested sessions sit in this vault, so the noise question can be answered by re-running the harvester over them with the line removed and counting what appears, before anyone ships anything. If it comes back noisy, the record-at-source sibling is the default, because it gets the same coverage without loosening any filter.

Ideated by an unattended pass on 2026-08-27 against the assigned dimension. **Not blind:** all three candidates under this opportunity were composed in one context by one author, because this surface holds no grant to run independent parallel ideators. Discount their apparent distinctness accordingly.
