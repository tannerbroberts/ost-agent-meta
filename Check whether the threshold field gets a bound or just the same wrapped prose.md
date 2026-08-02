---
type: AssumptionTest
source: 'agent-ideated:2026-08-02-maintenance-pass'
created: '2026-08-02'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Risk category: usability.** The node's own Issues entry names this follow-on and leaves it unrun; this is that test, written out.

**The assumption under test.** That giving the threshold a field changes what authors write, rather than just moving where they write it. The node's shipped half made the field optional on purpose, so nothing forces a bound — and its own honest worry is that whoever fills it in "just re-pastes the same hard-wrapped prose into the field," in which case the schema change bought a parse path and no clarity, while the misread it was meant to prevent survives one level down.

**Why this and not the migration question.** The migration was correctly declared unnecessary — the prose fallback makes it optional. The live risk is behavioural, not mechanical, and behaviour is not something the build can settle about itself.

**The test (observe what gets written, do not ask).** Over the next **15 AssumptionTest nodes** created with the field available — by any author, agent or human — classify each `threshold` value without telling the authors it is being classified:

- **bound** — a machine-comparable condition (a number, a count, a ratio, a yes/no);
- **prose** — a sentence that restates reasoning, wraps, or would need a human to interpret;
- **absent** — field not used at all, prose fallback carried the threshold.

**Pre-committed threshold.** **10 of 15 or more classify as `bound`** and the field is doing its job. **Fewer than 10** and the shipped half is confirmed as cosmetic: the honest response is to close this candidate rather than harden it, and to look instead at whether the *prose extractor* — which already found 65 of 77 here and 27 of 27 in the sibling vault — was adequate all along.

**What a result must also state.** Whether any of the 15 were authored by a human. If all 15 are agent-authored, the finding is about agent behaviour under a schema hint and says nothing about the human author this field was partly for.

**Cost note.** This test costs nothing to set up and only requires waiting — 15 nodes is roughly a few passes at this vault's observed rate. It should not block anything.
